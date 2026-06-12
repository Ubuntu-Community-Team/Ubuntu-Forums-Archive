---
title: "Ubuntu 11.10 Need help with error(attached)"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by Bobrm2 on 2012-06-01
installArchives() failed: Preconfiguring packages ...

Preconfiguring packages ...

Preconfiguring packages ...

dpkg: error: parsing file '/var/lib/dpkg/available' near line 4131 package 'python-zope.interface':

 error in Version string '0:3.6.1-dates for language English

 Translation data updates for all supported packages for:

 English

 .

 language-pack-en-base provides the bulk of translation data

 and is updated only seldom. This package provides frequent translation

 updates.': version string has embedded spaces

Error in function: 

SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


How do I clear this issue? and thank you. It has been a battle just getting to this point, after beginning attempts to upgrade to 12.04; there is some similarity in this error and the crash at the point of installing the "language Packs" in both 11.10 and 12.04 versions on computers other than AMD64's.
  I'm non-techincal. 

This may be a clue, with problems in downloading vers. 11.10 and 12.04?

---

### Post by Bobrm2 on 2012-06-01
This may shed further insight?

installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/available' near line 4131 package 'python-zope.interface':

 error in Version string '0:3.6.1-dates for language English

 Translation data updates for all supported packages for:

 English

 .

 language-pack-en-base provides the bulk of translation data

 and is updated only seldom. This package provides frequent translation

 updates.': version string has embedded spaces

Error in function: 

SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by Bobrm2 on 2012-06-01
This will add a clue, the last lines display the same error message that I struggled with for two days attempting to install first `12.04 and then returning to 11.10. It has something to do with the language packs. I can't now duplicate the error message, nor remember the "Bug" report issued by Source Forge.
  I have 301 files to be upgraded, possibility the solution is contain within one of them, for what ever good that does.

Bob



installArchives() failed: 
Extracting templates from packages: 9%%
Extracting templates from packages: 19%%
Extracting templates from packages: 29%%
Extracting templates from packages: 39%%
Extracting templates from packages: 49%%
Extracting templates from packages: 59%%
Extracting templates from packages: 69%%
Extracting templates from packages: 79%%
Extracting templates from packages: 89%%
Extracting templates from packages: 99%%
Extracting templates from packages: 100%%

Preconfiguring packages ...


Extracting templates from packages: 9%%
Extracting templates from packages: 19%%
Extracting templates from packages: 29%%
Extracting templates from packages: 39%%
Extracting templates from packages: 49%%
Extracting templates from packages: 59%%
Extracting templates from packages: 69%%
Extracting templates from packages: 79%%
Extracting templates from packages: 89%%
Extracting templates from packages: 99%%
Extracting templates from packages: 100%%

Preconfiguring packages ...


Extracting templates from packages: 9%%
Extracting templates from packages: 19%%
Extracting templates from packages: 29%%
Extracting templates from packages: 39%%
Extracting templates from packages: 49%%
Extracting templates from packages: 59%%
Extracting templates from packages: 69%%
Extracting templates from packages: 79%%
Extracting templates from packages: 89%%
Extracting templates from packages: 99%%
Extracting templates from packages: 100%%

Preconfiguring packages ...

dpkg: error: parsing file '/var/lib/dpkg/available' near line 4131 package 'python-zope.interface':

 error in Version string '0:3.6.1-dates for language English

 Translation data updates for all supported packages for:

 English

 .

 language-pack-en-base provides the bulk of translation data

 and is updated only seldom. This package provides frequent translation

 updates.': version string has embedded spaces

Error in function:

---

