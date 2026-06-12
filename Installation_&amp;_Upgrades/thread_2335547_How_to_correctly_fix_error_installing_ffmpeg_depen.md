---
title: "How to correctly fix error installing ffmpeg dependency Package?"
date: 2016-08-30
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2016-08-30
I am attempting to install a dependency for the ffmpeg package 

The dependency is libgnutls30 (version 3.5.3.2)


The error is: Breaks existing package 'libgnutls-openssl27' dependency libgnutls30 (=3.4.10-4ubuntu1.1)


Do I force install this specific dependency? If not, how do I get around this error? I cannot install any other dependencies for ffmpeg, nor can I install the complete ffmpeg package, until I get this error resolved. Also, extracting the dependency file and manually installing this specific dependency, either by replacing version 3.4.10, or manually installing as an addition to version 3.4.10, does not work as I still get both the error message and unable to complete full installation of ffmpeg and other related dependencies.

Thank you for any assistance you may be able to provide.

Lubuntu 16.04

---

### Post by roler2 on 2016-08-30
I did a force install however I would not recommended that. Fortunately, the files that were deleted by the force install, including the existing package as listed above (and there were three additional deleted files) had all been upgraded to 16.10 versions (and libgnutls30 is now at version 3.5.3.3). Also, it appears to me that certain 16.10 files can be installed within 16.04, as I have upgraded other files for other installed Programs that are specific to 16.10.

---

