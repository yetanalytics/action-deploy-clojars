# action-deploy-clojars
GitHub Action to deploy Clojure libraries to Clojars.

When invoked, the action will compile a JAR file that will be deployed to Clojars. The JAR will also be stored as a workflow artifact. The following demonstrates a call to this action with all required inputs:

```yaml
    steps:
      - name: Setup environment # You will need to call this action first
        uses: yetanalytics/action-setup-env@<tag>

      - name: Deploy to clojars
        uses: yetanalytics/action-deploy-clojars@<tag>
        with:
          artifact-id: 'my-library'
          version: '0.1.0'
          clojars-username: ${{ secrets.CLOJARS_USERNAME }}
          clojars-deploy-token: ${{ secrets.CLOJARS_DEPLOY_TOKEN }}
```

The following is a table of all inputs:

Name | Description
--- | ---
`artifact-id`          | The Clojars Artifact ID (i.e. the name of the lib itself). **Required**
`version`              | The version string. (By Clojars convention, you should remove any prefixes, e.g. the `v` in `v0.1.0`.) **Required**
`clojars-username`     | The Clojars username (should be a GitHub secret). **Required**
`clojars-deploy-token` | The Clojars deploy token (should be a GitHub secret). **Required**
`group-id`             | The Clojars Group ID. Defaults to `'com.yetanalytics'`.
`license-name`         | The license that the project is distributed under. Defaults to `Apache-2.0`.
`license-url`          | A URL that links to the text of the license. Defaults to `https://www.apache.org/licenses/LICENSE-2.0.txt`.
`src-dirs`             | A quoted array of the source directories. Defaults to `'["src/main"]'`.
`resource-dirs`        | A quoted array of the resource directories. Defaults to `'["resources"]'`. Pass `'[]'` if no resource directories exist.
`publish`              | Whether or not to actually publish to Clojars. Default `true`; turn off for debugging.
