---
title: "Lost Internet Connection After 14.04 Update for Network Manager"
date: 2016-05-14
forum: Installation &amp; Upgrades
---

### Post by facosta on 2016-05-14
Updated recent software updates that included libnm-util2, libnm-glib-vpn1,
network manager, gir1.2 network manager 1.0 and libnm-glib4. These packages
will not load due to "not being authenticated". Tried synaptic and gave 
warning about malicious packages. 

Tried various command lines:

sudo service network-manager restart

sudo apt-get --purge autoremove network-manager && sudo apt-get install network-manager

All have failed. How can I resolve my internet connection?

---

### Post by groverpm on 2016-05-14
This happened to me as well. It's made more difficult by my being a noobie. With no internet any attempts to fix the issue are useless.

---

### Post by facosta on 2016-05-14
I found the fix:

Open the terminal and run:
sudo apt-get --purge autoremove network-manager

Then follow the instructions in this link.
[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

You have to reinstall network manager. If the icon is still missing run:

nm-applet

The reboot your system.

---

### Post by de Bacon on 2016-05-14
Running Ubuntu-Studio 14.04.x, I have the same issue resulting from a small update yesterday.  I try to keep the software up to date, and the security update yesterday was small < 1Mb (for its download, if my memory serves, sometimes it doesn't)  Since I am running Ubuntu-Studio, rather than straight up Ubuntu, I wonder how I will need to alter the command stated in that help.ubuntu.com that is linked above.  Those instructions state this code:
            sudo apt-get install network-manager-gnome
where as Ubuntu-Studio is unlikely to be using Gnome as its network manager.  I don't know how to decipher this issue to know the correct code for re-instalation of the network manager if in fact Ubuntu Studio (somewhat based in xubuntu) uses a different form of network manager.  

Thanks for the assist to any who are able to help with this.

---

### Post by groverpm on 2016-05-14
> **facosta said:**
> I found the fix:

Open the terminal and run:
sudo apt-get --purge autoremove network-manager

Then follow the instructions in this link.
[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

You have to reinstall network manager. If the icon is still missing run:

nm-applet

The reboot your system.

This requires a working network which I don't have. I've downloaded 3 libnl files and put them on the desktop but can't install them. First I tried installing libnl-3-200_3.2.21-1_i386.deb using the following

sudo dpkg -i /desktop/libnl/libnl3-200_3.2.21-1_i386.deb

I get a cannot access archive: no such file or directory message. I'm stopping for today because otherwise  I'll smash hte desktop. Nothing I've tried works.

---

### Post by de Bacon on 2016-05-14
I have noted the same thing, no network doesn't allow getting files from the internet to fix.  Still my researching into this, reading other posts on the ubuntu forums site, shows this issue is wide spread.  I have yet to find a resolution also.  If/when I am able to resolve this I will post the links I followed here.  Maybe it I'll figure it out sooner than later?  Best of luck.

---

### Post by Bashing-om on 2016-05-14
et al; There are solutions.

Many have had success with:
[http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841](http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841)
going through the recovery console.

Then there is manually obtaining the new network-manager package via another system :
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634)
transfer the files to the broke system and install with 'dpkg -i ' .

[INDENT]many paths to an end
[/INDENT]

---

### Post by Bashing-om on 2016-05-14
er al ; There are solutions.

Many have had success with:
[http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841](http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841)
through "recovery mode" .

Then there is the manual way:
[https://launchpad.net/ubuntu/+source/network-manager/0.9.8.8-0ubuntu7.3](https://launchpad.net/ubuntu/+source/network-manager/0.9.8.8-0ubuntu7.3)
where the new network-manager package is downloaded onto another system and the files transferred to the broke system,
'dpkg -i' to install .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]many paths to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by de Bacon on 2016-05-14
I have somewhat fixed this problem by following the steps outlined here:  [http://ubuntuforums.org/showthread.php?t=2324421](http://ubuntuforums.org/showthread.php?t=2324421)
This is actually a downgrade to the network manager, yet it can get one back to having a connection to the Internet thus a place to work at gaining a real fix.

I found that the version of Recovery Mode in Grub 2 (on my system) has a problem, thus is fully unhelpful for me.  The program hangs after selecting an item then selecting the Yes with a click of its radio button.  I have an old version of Boot Repair and shall make a new current repair disc for boot loader, because I think that the version I have must be out of date (I have had that live disk for at least 4 years, maybe longer).   I don't know that it makes any difference with the version of boot repair, being ignorant of such things.  

I hope you can get your system up and running again before you smash it.  

Cheers,

---

### Post by groverpm on 2016-05-15
I have the required libnl packages but I can't install them because I don't know how to open the terminal in the folder they are in. They are in a folder on my desktop. When I open the terminal and enter
/~/paul/Desktop/libnl
I get the following:
Bash: /home/paul/Desktop/libnl: is a directory

So I enter

sudo dpkg -i  libnl-*.deb

And the response

dpkg: error in processing  archive libnl-*.deb
Cannot access archive: No such file or directory 
Errors were encountered while processing:
libnl-*.deb

I downloaded nautilus but can't install that either (used the software center for that). So how do I openthe terminal in a specific folder?

Ftr I'm using my mobile to use this forum and download the files needed.

I can now open the terminal in the correct folder however I get error messages when trying to install the libnl, libnl-gen, and libnl-route archives. Apparently they are not a debian format archive despite being downloaded via this forum. If I had hair I'd be ripping it out now.

---

### Post by de Bacon on 2016-05-15
groverpm, 

It does take a while to figure out how to make Linux go if you are uneducated in computering.  I understand how you likely feel, been there and had many struggles.  Too many assume the user knows this and that.  

So I am now wondering why.  I went through this process yesterday, and truly it is only a patch, not really a fix.  I get error messages when I first log in but the ethernet connection is working. 

I will preface this with, I am not an expert and I may not fully understand your situation with the information you have provided.  Nor do I know how to use this system well, where some can put code in little separation boxes, I don't know how to do that in this forum.  

Were it me, I would delete those three files from your desktop folder and download them again.  There should be no problem with putting them in the Desktop folder.  

You say you can now open a terminal and change its directory.  Is that done with the command "cd" = _c_hange _d_irectory.  Here is a list of commands [http://ss64.com/bash/]("http://ss64.com/bash/"). There may be better lists of commands with better explanations out there but...  

I just read your other post, stating the same issue.  I am thinking that maybe you need the 64 bit files rather than the 32 bit ones you accessed.  Try it again, I don't understand why you would get an error message as you have described. 

The real test comes when we do the next update of the system, is it fixed or will it happen again.  Like you, I checked to see the settings in my software center properties, the correct box is unchecked as it has been for several years.  

Best of luck with fixing your machine.

---

### Post by groverpm on 2016-05-15
My pc is 32bit so I assume the i386 files are the correct  ones. However since they haven't    worked I'll try the 64bit options. That will have to wait 'til tomorrow. I've been trying all day and if it doesn't work my pc will probably end up being thrown from the 4th floor balcony if I continue today. 
Ftr, I did use the cd  command. 
Thanks de Bacon. I will post the results  tomorrow but I don't have much faith it will help.

---

### Post by de Bacon on 2016-05-15
If in fact you know that you have 32 bit, maybe there was a problem with one or more of those downloads, causing its load to fail.  I'd try deleting them all and downloading them again before your next attempt.

---

### Post by groverpm on 2016-05-16
Nothing works. After downloading  the required packages both from the numerous download links on this forum and directly from packages.ubuntu.com I still get the same error messages. I will now uninstall  the ubuntu ssd and reinstall the windows 7 ssd.

---

