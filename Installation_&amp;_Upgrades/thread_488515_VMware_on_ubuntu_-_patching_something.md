---
title: "VMware on ubuntu - patching something?"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by Thorun on 2007-06-30
Hi. 

I'm trying to install VMware on my Ubunt-FF. And i have read, that there should be a bug in the synaptic/automatix-versions. Therefore i'm following a step-by-step guide to install it. 
Now i need to patch something but i have no idea of what they mean with that:

The guide i'm following:
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

The link to how to patch:
[http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)

It's this phrase i don't understand:
"After downloading unpack file into some directory, enter that directory and run "./runme.pl". After doing that run "vmware-config.pl", or,..."

Could someone tell me how i "run" the ./runme.pl?  I have placed the folder on the desktop and un-tar'ed it there too. 
And how do i run the "vmware-config.pl" ? In a Terminal? and in what directory??
and... 
I'm only 3 weeks old with ubuntu but would like to have Win98 and WinXP installed too with VMware.


Edit:
When i open a Terminal and type: sudo ./runme.pl i just get:

```
rune@dell-uff:~/Desktop/VMware-stuff/vmware-any-any-update109$ sudo ./runme.pl
Unable to open the installer database /etc/vmware/locations in read-mode.

Execution aborted.
```

---

### Post by devnu11 on 2007-06-30
I assume the file was called something like any-any.  I believe I just uncompressed the tar.gz file and sudo /runme.pl  Do you have pearl installed as I would guess .pl is a perl file.

I could be wrong but I believe the script merely replaces vmmon.tar in:
/usr/lib/vmware-server/modules/source/vmmon.tar

and vmnet.tar in:
/usr/lib/vmware-server/modules/source/vmnet.tar


you could do something like cp /usr/lib/vmware-server/modules/source/vmnet.tar /usr/lib/vmware-server/modules/source/vmnet.tar.orig and 
cp /usr/lib/vmware-server/modules/source/vmmon.tar /usr/lib/vmware-server/modules/source/vmmon.tar.orig

and manually copy the new files vmnet.tar and vmmon.tar to /usr/lib/vmware-server/modules/source/ and try installing again.

Good luck

---

### Post by Thorun on 2007-06-30
Uhm...
It could be that you're right. 

I haven't installed VMware yet, though. 
My question was about what they mean with :

> Download newest file which matches system you are using: currently it is simple, just grab latest vmware-any-any-update*.tar.gz file you can download.

After downloading unpack file into some directory, enter that directory and run "./runme.pl". After doing that run "vmware-config.pl", or, if you installed update on system which is supported by your product (though I do not understand why you installed product in this case) "vmware-config.pl -compile". Note that while original modules from VMware do not need C++ compiler, my updates need it, and won't build without - it is price I had to pay to get support for all these products from one source.

After that your kernel should not complain about problems with kernel modules anymore, and everything should run as on supported host.


And this from the VMware guide:
> Downloading VMware Server
Vmware Server can be downloaded from:
[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)
After accepting the EULA grab the vmware server .tgz file (around 102MB).

[B]Note: As of right now VMware Server won't compile correctly on Feisty without patching the vmmon file.
[/B]
Patch information can be found here: [http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)

The patch can be downloaded here: [http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)



If you do think that your answer is the correct one to this answer, i'm sorry I have made this reply. I'm just confused if i can "swap" files in a directory that i haven't made yet....
But I don't know - as i have not tried your suggestion yet.

---

### Post by disrupta on 2007-07-02
i got the exact same problem and am and have been using the exact same guide. 

if i resolve it by attempted to follow the instructions above ill let you know. 

im wondering is this the best order to do it in, but it does say you need to do it first. that directory doesn't exist yet. so there are some steps missing. 

my first post i'm sure to be using this more. just got beryl working. but i really want vmware working 2. ive used vmware before but not on ubuntu. Its fantastic tho.

---

### Post by disrupta on 2007-07-02
lil update 
i got this exactly still

rune@dell-uff:~/Desktop/VMware-stuff/vmware-any-any-update109$ sudo ./runme.pl
Unable to open the installer database /etc/vmware/locations in read-mode.

Execution aborted.

and then ive tried the below in many different possible ways. different terminals, su and as root. as a nautilus window. 

you could do something like cp /usr/lib/vmware-server/modules/source/vmnet.tar /usr/lib/vmware-server/modules/source/vmnet.tar.orig and
cp /usr/lib/vmware-server/modules/source/vmmon.tar /usr/lib/vmware-server/modules/source/vmmon.tar.orig

and manually copy the new files vmnet.tar and vmmon.tar to /usr/lib/vmware-server/modules/source/ and try installing again.

it comes up wid this 
root@core2duo-desktop:/vmware-any-any-update109# cp /usr/lib/vmware-server/modules/source/vmnet.tar /usr/lib/vmware-server/modules/source/vmnet.tar.orig
cp: cannot stat `/usr/lib/vmware-server/modules/source/vmnet.tar': No such file or directory

i go in to manually make the directory cntrol alt n ect there is just no option to make directory. 

im going to skip this step at moment let you know how far i get and go. 
at moment i simply can't do this with the information i can find. 

ps im gonna persist a little more to make the directory and copy the files in manually. but i can't work out how at moment

---

### Post by disrupta on 2007-07-02
cant proceed with that guide

core2duo@core2duo-desktop:/ok/vmware-server-distrib$ sudo vmware-install.pl
sudo: vmware-install.pl: command not found
core2duo@core2duo-desktop:/ok/vmware-server-distrib$ ls
bin  doc  etc  FILES  installer  lib  man  sbin  vmware-install.pl  vmware-vix
core2duo@core2duo-desktop:/ok/vmware-server-distrib$ 

cant do this part

Run the installer:

sudo vmware-install.pl

again its a .pl file. perl or pearl. it looks like we need a perl installer i guess like you mentioned above. so looking 4 that now. ill let someone else message back now.

---

### Post by disrupta on 2007-07-02
did this and this to install perl

sudo aptitude install perl
sudo cpan install Date::Manip

still doesn't run. far from easy. im persisting.

---

### Post by Thorun on 2007-07-02
@Disrupta

I've just made it work. Now wery well - but i have VMware installed. Allthough i have a win98 installation on it now - and it runs wery slow - but that's yet another problem. 


I've got an personal msg. from somebody. It says:
> There is a better way!

This is the problem with the phrase "as of right now".  It may have
 been accurate at time of writing, but when was that?

As of right now (1 July 2007) the best way to install vmware server
 under ubuntu is via the commercial repository.  You need to do two things:

1.Add the commercial repository to the list.  This has to be done by
 editing the data file manually.
2.Install vmware server from synaptic.

I can't include full instructions in a pm, but if you search the forums
 for "vmware server repository" I'm sure they are there somewhere.

Cheers


And what he means with the number 1 is this:
Edit some file manually:
```
sudo gedit /etc/apt/sources.list
```
Add the line:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```
Now you need to update Ubuntu Source List using the following command
```
sudo apt-get update
```

I did it without the third part (apt-get update) and run the installation from Synaptic (with a reload) and it just installed smoothly.


The things you have to add to some repository i've got from this guide:
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

---

### Post by disrupta on 2007-07-02
read this 

[http://ubuntuforums.org/showthread.php?t=220154&page=2](http://ubuntuforums.org/showthread.php?t=220154&page=2)
sudo sh vmware-install.pl
sudo ./vmware-install.pl

the above makes it run

but at the end of the day 

make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

you get the above. 

so you do really need this run to work. 

i still cant make it run
no way we can skip it, it is an essential step. looking for answers. totally stuck now

---

### Post by Thorun on 2007-07-02
If you try with my latest reply (just above your last pos) It should work. 

Offcourse when one have tried to install it over and over again, one need to delete the existing direcotries.  Hence  ```
rm -r /something/something/vmware
```
And then try the above description. 

add the line to the repository as described. Update via the terminal. Open up Synaptic and install VMware server.

The ubuntugeek's website made my day (yesterday). 
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

---

### Post by disrupta on 2007-07-02
thanks for that !!  much appreciated 

I have it running now too. i got it installed. 

This forum has been invaluable to me. And thanks for the quick reply. i did those things you mentioned in that message. Your help has proved exactly what I needed!. 

Hopefully if anyone else has the problem or question they can read between the lines in this forum and it can help them too. 

For now its working! Thanks for the quick reply! Excellent. Much Appreciated!

---

