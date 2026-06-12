---
title: "Can't dual boot"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2011-05-29
I unplugged the Windows drive, during the installation of Ubuntu 9 (to  make things easier). 2 separate drives. When installation was complete, I  plugged the other drive back in (now both are plugged in). I went to  the BIOS and made sure the Linux drive was the set to boot before the  windows drive. The only thing that comes before that of course is the cd  drive

CD-0
HDD-1 (linux)
HDD-0 (windows)

I booted into linux after this and ran 'sudo update-grub'. The cmd was  successful. However, when rebooting it does not give me the option to  boot to windows. Why not?

PS. If I go to Places (under GNOME bar), Then I can see (and mount) the windows drive. So it is accessible.

---

### Post by Quackers on 2011-05-29
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder).
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kakashi_12 on 2011-05-29
nvm, I just re-installed linux with the drive plugged in this time. at the end of installation, it prompted me to install grub to the mbr of the the windows drive. i think thats where the mistake was before.

---

