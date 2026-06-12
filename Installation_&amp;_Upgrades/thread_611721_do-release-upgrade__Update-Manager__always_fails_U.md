---
title: "do-release-upgrade / Update-Manager  always fails Upgrading"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by BenderIII on 2007-11-13
Hi,

I've just finished reading various postings regarding the update-manager problem to 7.10 I have but found no solution.

Current install is 7.04 server with a minimal vncserver to get some gui-progs running without installing the whole desktop system. 'Cause I don't need all the stuff in it.

  Then tried to use update-manager to upgrade and always failed to finish.


What I've done so far:

- First updated to the latest 7.4 feisty. 
- executed do-release-update several times.
   After several unsuccessful runs I tried Update-Manager and it shows the same errormessages.
  [ Hell, for what I need 1GB of ubuntu-desktop to upgrade?????]

 One time the upgrade stops in the first part with the message, that the Prerequists couldn't installed correctly. Other times I got an ErrorCode 2 of Subprocess while processing archivename.bz2 :(

After I had seen what errors are shown I tried to manually download the failed packages with wget and check them with bzip2.   In rare cases the error has gone once. But mostly there was an CRC-Error in the package.    
Just for the complete test I checked my memory modul (1GB) but all fine here. CPU tests also shows no errors. Network should be ok, as I had no errors while using it from a notebook with XP.
 My last check for the corrupted packages was a run with CURL archive.deb  èt voilà every former corrupted package was in a valid condition everytime I downloaded them. 

that makes me big :confused: 

Can somebody explain me (as I haven't found yet) how apt-get/do-release-upgrade/update-manager are downloading the archieves from the web? Because if it's a problem related to wget than I have no conclusion how to solve it. Even a reinstall of wget hasn't changed anything :(

But I would patch the install script using curl :). And manually downloading all required archieves is no option as the upgrade-manager always creates a new tmp-dir.

Btw, updating via cdromupdate has the same problems as some data is fetched from the web even if I choose to not use updated files.

---

