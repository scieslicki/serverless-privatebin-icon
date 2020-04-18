You can automate the favicon creation using a Node.js command-line interface:

1. Install cli-real-favicon:
`npm install -g cli-real-favicon`

2. Create a file named faviconDescription.json and populate it with:
```
{
	"masterPicture": "TODO: Path to your master picture",
	"iconsPath": "/",
	"design": {
		"ios": {
			"pictureAspect": "backgroundAndMargin",
			"backgroundColor": "#ffffff",
			"margin": "14%",
			"assets": {
				"ios6AndPriorIcons": false,
				"ios7AndLaterIcons": true,
				"precomposedIcons": true,
				"declareOnlyDefaultIcon": true
			},
			"appName": "Szotki"
		},
		"desktopBrowser": {
			"design": "raw"
		},
		"windows": {
			"pictureAspect": "whiteSilhouette",
			"backgroundColor": "#da532c",
			"onConflict": "override",
			"assets": {
				"windows80Ie10Tile": false,
				"windows10Ie11EdgeTiles": {
					"small": false,
					"medium": true,
					"big": false,
					"rectangle": false
				}
			},
			"appName": "Szotki"
		},
		"androidChrome": {
			"pictureAspect": "backgroundAndMargin",
			"margin": "8%",
			"backgroundColor": "#ffffff",
			"themeColor": "#ffffff",
			"manifest": {
				"name": "Szotki",
				"display": "browser",
				"orientation": "notSet",
				"onConflict": "override",
				"declared": true
			},
			"assets": {
				"legacyIcon": false,
				"lowResolutionIcons": true
			}
		},
		"safariPinnedTab": {
			"pictureAspect": "silhouette",
			"themeColor": "#5bbad5"
		}
	},
	"settings": {
		"scalingAlgorithm": "Lanczos",
		"errorOnImageTooSmall": false,
		"readmeFile": true,
		"htmlCodeFile": true,
		"usePathAsIs": false
	}
}
```

3. In the code above, replace `TODO: Path to your master picture` with the path of your master picture. For example, `assets/images/master_picture.png`.

4. Generate your icons:

```
mkdir dist
real-favicon generate faviconDescription.json faviconData.json dist`
```

5. Inject the HTML code in your pages:

`real-favicon inject faviconData.json dist htmlFiles/*.html`

6. Check for updates (to be run from time to time, ideally by your continuous integration system):

`real-favicon check-for-update --fail-on-update faviconData.json`

7. Optional - Your favicon is fantastic. 

