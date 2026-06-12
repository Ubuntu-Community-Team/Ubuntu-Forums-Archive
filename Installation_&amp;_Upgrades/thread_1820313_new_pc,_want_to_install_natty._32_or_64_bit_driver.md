---
title: "new pc, want to install natty. 32 or 64 bit? drivers?"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by supermeow on 2011-08-07
hi there,

i am about to install ubuntu on a newly bought pc (1 hour ago.. and already hate windows, as usual).

here' the specifics...(just copied them... i am really ignorant on this stuff)

this is a HP pavilion g6
RAM 4GB
processor intel core i5 - 2410M cpu at 2.30Ghz
system 64 bit
hard rive is NTFS, 600 GB
ATA = intel mobile express chipset Sata Ahci Controller

i used to have ubuntu on another hp laptop, which started great with karmic and went downhill straight.. up to the last maverick (blank screen, grub not loading, kernel problems, video drivers for nvidia not working... all sort of frustrations)... so after a long fight, the old laptop ended in my trash bin (i really lost it...) and here's the new one.

question: what shall i install? 32 or 64 bit?
i'm really not a tech guy (i mean i ended up smashing my old laptop out of frustration...) and when it comes to stuff like grub, bootloader, partitioning, drives, ... i can just copy/paste instructions on the terminal... so, any help in plain (very plain, non-tech) english would be highly appreciated.

also... how can i make sure the iso file will be burned properly (i am using a freshly bought laptop with pre-installed windows 7) and that i will find appropriate drivers for this pc once i install natty (btw, should i install natty at all?)

thanks a million for any feedback

Cheers

---

### Post by oldfred on 2011-08-07
No reason not to install 64bit. Issue may be what video do you have so you need to test liveCD or liveUSB to see if you need custom settings or not.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You probably have all 4 primary partitions used, so you have to decide what partition to delete.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

You may not ever need recover DVDs, but you should have them. But you may need a repair CD, so that is vital to make.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by supermeow on 2011-08-07
wow... that is a lot to read and learn there... 
well, thanks a lot for the answer... so, i take it i can not just go with the simple option "erase and use entire disk"... or i would mess up this new laptop, right? so i have to learn about partitioning now...

one more question: i have been watching video reviews of various linux distributions (mint, mandriva, fedora, elementary-jupiter, suse...)

as i know ubuntu 11.04 natty seems to have lots of problems with drivers and stuff... would any of those alternatives be better for a fres install (provided i learn how to make a windows repair cd and learn how to partition the drive...)?


if anyone can answer...
i am looking for something possibly elegant (like mandriva or fedora seem to be), with the possibility of working in different languages (i have to use docs and other stuff in korean/japanese/chinese and other languages i am studying), thus supporting several fonts... with a simple graphic editor like pinta... and with a decent music player which would also sync with ipods... and... overall a system which is easy to use  (say, easy as ubuntu 9 or 10)..  hope i am not asking for something impossible...

thanks again

---

### Post by x-D on 2011-08-07
> **supermeow said:**
> wow... that is a lot to read and learn there... 
well, thanks a lot for the answer... so, i take it i can not just go with the simple option "erase and use entire disk"... or i would mess up this new laptop, right? so i have to learn about partitioning now...

one more question: i have been watching video reviews of various linux distributions (mint, mandriva, fedora, elementary-jupiter, suse...)

as i know ubuntu 11.04 natty seems to have lots of problems with drivers and stuff... would any of those alternatives be better for a fres install (provided i learn how to make a windows repair cd and learn how to partition the drive...)?


if anyone can answer...
i am looking for something possibly elegant (like mandriva or fedora seem to be), with the possibility of working in different languages (i have to use docs and other stuff in korean/japanese/chinese and other languages i am studying), thus supporting several fonts... with a simple graphic editor like pinta... and with a decent music player which would also sync with ipods... and... overall a system which is easy to use  (say, easy as ubuntu 9 or 10)..  hope i am not asking for something impossible...

thanks again

No, you can go with the 'simple', use all space method. All it will mean is that you will delete Windows and only Ubuntu will be left.

Is this what you want? If so, then using all the space - is the BEST option for you, and your setup! :) 

Hope this helps....

x-D :guitar:

---

### Post by x-D on 2011-08-07
> **supermeow said:**
> wow... that is a lot to read and learn there... 
well, thanks a lot for the answer... so, i take it i can not just go with the simple option "erase and use entire disk"... or i would mess up this new laptop, right? so i have to learn about partitioning now...

one more question: i have been watching video reviews of various linux distributions (mint, mandriva, fedora, elementary-jupiter, suse...)

as i know ubuntu 11.04 natty seems to have lots of problems with drivers and stuff... would any of those alternatives be better for a fres install (provided i learn how to make a windows repair cd and learn how to partition the drive...)?


if anyone can answer...
i am looking for something possibly elegant (like mandriva or fedora seem to be), with the possibility of working in different languages (i have to use docs and other stuff in korean/japanese/chinese and other languages i am studying), thus supporting several fonts... with a simple graphic editor like pinta... and with a decent music player which would also sync with ipods... and... overall a system which is easy to use  (say, easy as ubuntu 9 or 10)..  hope i am not asking for something impossible...

thanks again

Natty might be slightly more buggy, but NOTHING is more user friendly than Ubuntu. If you're worried about the bugs, I've heard 'Xubuntu' and 'Kubuntu' have had REALLY low bug amounts :) 

Hope this helps....

x-D :guitar:

---

### Post by supermeow on 2011-08-07
thanks... that's kind of... what i needed to hear ... just get rid of windows :-)

i think i would go with using the entire disk.... after all it's just a new laptop... there is nothing in it except windows and all my files are stored in an external HD.

and yeah, no doubts on ubuntu, though natty was messy for me....i just was trying to understand which flavour would suit my needs better (mandriva, mint, fedora...now i saw some other stuff called penguin.... and another called jupiter.... there are so many ubuntu out there... just don't know which one to choose)

i would like to know which one of these alternative ubuntu versions could work well at 64bit...

thanks a million for all the feedback

---

