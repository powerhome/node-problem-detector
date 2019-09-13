# Change Log
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/).

## [0.3.0] - 2019-09-13
### Added
- Add support to parse values from the event message and add in the event annotation.

    Add field `valuePatterns` where you can specify multiple values to be extracted from the message. It will only retrive the first group. For example:

    ```
        "rules": [
            {
                "type": "temporary",
                "reason": "KernelOops",
                "pattern": "BUG: unable to handle kernel NULL pointer dereference at .*",
                "valuePatterns": {
                    "v1": "NULL ([a-z]*)",
                    "v2": "(NULL [a-z]*)"
                }
            }
        ]
    ```

    This rule would add the values `v1: pointer` and `v2: NULL pointer` to the kube event annotation.

### Changed
- Update a few packages version to be able to use AnnotatedEventf instead of Eventf.
- Update k8s.io/api version to kubernetes-1.15.0
- Update k8s.io/apimachinery version to kubernetes-1.15.0
- Update k8s.io/client-go version to kubernetes-1.15.0


## [Unreleased]
### Added
- Add travis presubmit test.

### Changed
- Update kubernetes version to v1.4.0-beta.3

## [0.2.0] - 2016-08-23
### Added
- Add look back support in kernel monitor. Kernel monitor will look back for
  specified amount of time to detect old problems during each start or restart.
- Add support for some kernel oops detection.

### Changed
- Change NPD to get node name from `NODE_NAME` env first before `os.Hostname`,
  and update the example to get node name from downward api and set `NODE_NAME`.

## 0.1.0 - 2016-06-09
### Added
- Initial version of node problem detector.

[Unreleased]: https://github.com/kubernetes/node-problem-detector/compare/v0.2...HEAD
[0.2.0]: https://github.com/kubernetes/node-problem-detector/compare/v0.1...v0.2
