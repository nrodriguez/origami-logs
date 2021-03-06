<p align=center><img src="https://s15.postimg.cc/dk2ezad5n/logo.png" width="400"></p>

# Origami Logs

A github changelog generator for your release notes.

[![Build Status](https://travis-ci.org/xogroup/origami-logs.svg?branch=master)](https://travis-ci.org/xogroup/origami-logs)

## Installation

```npm i -g origami-logs```

## First Step

Create a file named `.origami-logs-config.json` in the root of your project.

The file should look something like this:

```
{
  "github":{
    "apiUrl": "https://git.somedomain.com/api/v3",
    "token": "123456",
    "repository": "Organization/repo-name"
  }
}
```

## How to use

TO RUN:

```
changelog generate --tags "startingTag,endingTag"

```

To see all other options:

```
changelog generate --help
```

## Config Options Explained

If you wish to add other config options it might look like this:

```
{
  "github":{
    "apiUrl": "https://git.somedomain.com/api/v3",
    "token": "123456",
    "repository": "Organization/repo-name"
  },
  "aliases": {
    "enhancement": [
      "feature"
    ]
  },
  "extraLabels": {
    "chore": "Chores Completed:"
  },
  "extras": {
    "pivotal":{
      "boardID": "1234567"
    }
  }
}
```

* `github`: *REQUIRED* The info about the given repository you wish to get the changelog format for markdown
* `aliases`: This is to be used if you want to use your own custom labels but still conform to the enhance/bug format.
  * IE: You might have a feature label but still want it to show `Features Implemented` on the changelog.
* `extraLabels`: Define your own custom labels and changelog headings
* `extras`: Where additional connections live
  * `pivotal`: Supports linking pivotal stories in your change log assuming commits conform to the format:
    `[#STORY_ID_HERE] Commit Message here`
    * `boardID`: Pivotal Board ID (Found at the end of the url such as `https://www.pivotaltracker.com/n/projects/ID-HERE`)
    
    
    
## Development

To test locally run
```
node cli.js generate --tags "TAG1,TAG2"
```
