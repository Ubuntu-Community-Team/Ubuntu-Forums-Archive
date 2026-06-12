---
title: "Multiple installation attempts failed miserably"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by KLG on 2005-07-07
I know that this the worst thing to do in a forum

repost a thread in a different section...

but i have no choice.. I think that ppl who want to help would check more often the installation section than the laptop section...

[http://ubuntuforums.org/showthread.php?t=46950](http://ubuntuforums.org/showthread.php?t=46950)

I have made actually 3 or more attempts and it always stops in one of the above points...

I have already downloaded the iso file from a different mirror and burned it in 4x

Please HELP!!!!!!!!!!!! ](*,)  ](*,)  ](*,)

---

### Post by javiadip on 2005-07-07
did you match the checksums after installing an iso? iso image could be corrupted.

---

### Post by KLG on 2005-07-07
checksums? i ve downloaded the german and ireland mirror iso's

and all the problems occure on the 1st startup.... after the installation

...when it is unpacking all the packages

---

### Post by javiadip on 2005-07-07
yea, but after you download....just do the md5 checksums

---

### Post by mingus on 2005-07-07
[QUOTE=KLG]
...when it is unpacking all the packages[/QUOTE]

During the installation, when you come to the step for installing packages, you will be asked where to get the packages from.  I'm sorry I can't remember exactly the screen or the dialogue.  My first install I missed this, my network was not yet set up, and as a result I got a lot of errors and had missing packages.  If you tell the installer not to use the net, it will pull the packages from the CD instead.

---

### Post by KLG on 2005-07-07
sorry for the delay, but i didnt have a clue about md5, so i had to google it out...

i downloaded fustsum 1.2 and did a checksum in the downloaded iso file, here are the results

Calculating process has begun at 8/7/2005 3:39:08 pm
Detecting size:Found 4 files in 0 folders with total size 586,93 MB
Calculating the checksums...
Calculation completed at 8/7/2005 3:39:59 pm
Processed 4 files in 0 folders with total size 586,80 MB

bad news?

---

### Post by KLG on 2005-07-07
mingus >> the network in my last attempts is set OK beacause the system gets time from ntp.ubuntu.... (no *ror temporary failure in name resolution occurs)

I closed dhcp and configured manually the ip settings and it worked

---

### Post by Gary Powers on 2005-07-07
[QUOTE=KLG]mingus >> the network in my last attempts is set OK beacause the system gets time from ntp.ubuntu.... (no *ror temporary failure in name resolution occurs)

I closed dhcp and configured manually the ip settings and it worked[/QUOTE]

KLG, I think you got the wrong "sum".  What you are looking for is a long string of letters/numbers which are obtained by running the md5sum program against your download.  Then, you compare that number against the md5sum which you will find from the location you downloaded the file.

Try this link for a Windows based md5sum program:

[www.irnis.net/gloss/md5sum-windows.shtml](www.irnis.net/gloss/md5sum-windows.shtml)

Let us know how it goes.

Gary

---

### Post by KLG on 2005-07-07
Ok, where do i find the md5 tags from the original file to compare them with my file ?

---

### Post by KLG on 2005-07-07
I am going to sleep now, thanx for your help, CU tomorrow

---

### Post by crashtest on 2005-07-07
[QUOTE=KLG]Ok, where do i find the md5 tags from the original file to compare them with my file ?[/QUOTE]

The md5sums are in a file inside the 5.04 directory on the download site.  The file is called md5sums.  I compared, and the md5sum you listed does match the i386 iso.
This would indicate the iso file you downloaded is good.


f6b3f164c99761234858a4d2c12d0840  ubuntu-5.04-install-i386.iso

---

### Post by Lax D Unit on 2005-07-08
ok ive had the exact same prob as this guy. if you look at my other posts. ive checked the md5 sums and cant make heads or tails of it. i can say that after downloading it 5 times with no dowload accelerator or anything im very frustrated to see all 5 fail. i would like to specify that i am downloading off a wireless network. i dont kno if that could be the cause of it but if u are downloading off a wifi network maybe thats why we both have the same prob.... i also had this prob downloading debian

---

### Post by KLG on 2005-07-08
No, I am downloading to a computer that gives internet to 2 other wirelessly

---

### Post by mingus on 2005-07-08
KLG,

You've have verified the md5sum and you fixed your network setup.  And you are installing in English.  So now try a fresh install in Expert mode.  Where *exactly* do you get your first errors?

You might also try to run the Live-CD and after you are logged into Gnome, immediately get into a terminal and do:
$dmesg | more
there you will see some boot messages; look for any hardware errors.

---

### Post by KLG on 2005-07-08
The installation finishes with no faults...

Then a msg "Put OUT (edited) the CD to continue" and "Preparing to start ubuntu for the first time is prompted" (or something like that...)


then it is starting to load

the first time it crashed when unpacking the openoffice...

the next times it crashed before unpacking the openoffice.... while setting xserver-xorg ....
then i set correctly the net and made an installation in english, and used the partitions ubuntu has proposed.... and it crashed again in ANOTHER!!! package after it had unpacked openoffice.....

I can't logon in Gnome... because i am forced to shutdown--(power button) the ctrl-alt-del works but it crashes after a while

---

### Post by mingus on 2005-07-08
I don't know why you keep getting failures on the installation of some packages . . . the fact that you can run the Live-CD is not related because it does not install anything.

Suggestion:  Boot and at the grub menu choose "Recovery".  At the prompt do:
#base-config

This will run the second stage of the installation (when you get to the "remove CD and reboot" that is only the completion of the first stage; you're install is failing in the second stage).

When you get to the screen asking for sources, insert the install CD and choose CD.  Do not install from the repository sources at this time.

---

### Post by KLG on 2005-07-08
the recovery fails too

I made 2 attempts in expert mode, in both i configured it to do the first startup without reboot, and not to copy the packages from the CD to HDisk.... Te 1st using greek language the 2nd in american english, Both crashed in xserver-xorg giving the following error:

sxerver-xor error unable to configure keybord layout '__ '

What shall i choose?

en_US or en_US UTF 8 ?

---

### Post by mingus on 2005-07-08
*en_US or en_US UTF 8 ?*

Choose all three of the en_US locales.

---

### Post by KLG on 2005-07-08
I said why don't i try server mode install?

so i tried it and left home to have a drink

and i return now and i see:

login:

IT ACTUALLY WORKED...

Do i have any chance installing the packages manually?

---

### Post by mingus on 2005-07-09
LOL, installing in server mode was going to be my next suggestion  :grin:  . . .

Yes, you can install what you need now manually.  I have not done this myself, but from other forum threads I have read, I think there are meta packages, for example, to install the desktop.  Sorry, I don't know the names of those packages, but I'm sure you can find them in the forums or the wiki.

---

