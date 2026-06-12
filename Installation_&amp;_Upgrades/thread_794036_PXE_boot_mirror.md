---
title: "PXE boot mirror"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by mic159 on 2008-05-14
I was following these instructions to install xubuntu using PXE
[https://help.ubuntu.com/community/PXEInstallServer]("https://help.ubuntu.com/community/PXEInstallServer")

BUT i got to "Choose a mirror for the ubuntu archive" section and it said that my mirror "is not available, or does not have the valid Release file on it."

All my "mirror" is, is a apache server running on the same computer as the tftp server, with a folder with all the files from the xubuntu-alternate cd, like in the instructions.

What should the layout of my mirror be? and why dosnt those instructions work?

---

### Post by dstew on 2008-05-14
Are you sure you used the correct IP address in your ks.cfg and pxelinux.cfg/default files?

---

### Post by mic159 on 2008-05-14
dstew, thanks for that, i had a trailing / at the end of the url when it shouldnt

now i fixed that and it starts to install, but now it 404s at one part :S

here is the errors in the syslog:
> anna[6390]: DEBUG: ask for nic-restriced-firmware-2.6.24-16-generic-di, matches kernel
anna[6390]: DEBUG: install nic-restriced-firmware-2.6.24-16-generic-di, priority >= standard
anna[6390]: DEBUG: ask for nic-restriced-modules-2.6.24-16-generic-di, matches kernel
anna[6390]: DEBUG: install nic-restriced-modules-2.6.24-16-generic-de, priority >= standard
anna[6390]: DEBUG: resolver (efi-modules): package doesn't exist (ignored)
anna[6390]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
anna[6390]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
anna[6390]: DEBUG: resolver (efi-modules): package doesn't exist (ignored)
anna[6390]: wget:  
anna[6390]: server returned error 404: HTTP/1.1 404 Not Found ^M
anna[6390]: 
anna[6390]: WARNING **: package retrieval failed


EDIT: ok, i presse change mirror and now it gives me a clearer error in the log:
> choose-mirror[8099]: DEBUG: command: wget -q http://192.168.0.1/xubuntu//dists/hardy/Release -O - | grep ^Suite: | cut -d' ' -f 2
choose-mirror[8099]: DEBUG: command: wget -q http://192.168.0.1/xubuntu//dists/hardy/Release -O - | grep ^Codename: | cut -d' ' -f 2
choose-mirror[8099]: INFO: codename set to: hardy
choose-mirror[8099]: DEBUG: command: wget -q http://192.168.0.1/xubuntu//dists/hardy/main/binary-i386/Release -O - | grep Architecture
anna[6390]: wget:  
anna[6390]: server returned error 404: HTTP/1.1 404 Not Found ^M
anna[6390]: 
anna[6390]: WARNING **: package retrieval failed

I tried ```
wget http://192.168.0.1/xubuntu//dists/hardy/main/binary-i386/Release
``` just in a terminal and it gets it fine.

---

### Post by mic159 on 2008-05-15
OK, dont worry, it all works now.

I had a look in teh apache access logs to see what exactly went wrong, and it turnes out that its only the ones with long filenames were not working.

This was because they were missing characters at the end of the filename. i suspect this occured when i was unpacking the ISO on the server computer (running win98), and it not supporting the long filenames.
So i just put back in the rest of the filename and it worked, i dont know why it didnt support the long filenames because after i renamed them, it didnt have any issues :D

it was the udeb ones because they have rather long filenames.

---

### Post by dstew on 2008-05-15
Thanks for the update. Possibly some of the file tranfer programs, like tftp, that are used in a PXE install might not be happy with long or unusual file names. Samba also comes to mind. I once had a directory with one file name that had a trademark (TM) symbol in it, and I could not even get a directory listing with smbclient until I figured that out...

---

