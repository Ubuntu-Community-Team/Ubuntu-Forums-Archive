---
title: "Wubi 14.10 - Workaround possible?"
date: 2014-11-08
forum: Installation &amp; Upgrades
---

### Post by anhyb on 2014-11-08
Hello everybody,

I know... Wubi is bad... Wubi is dead... Wubi is lame... Wubi is hated by everybody and very dangerous, it fails on EFI hardware, everybody sings: "No Wubi - No cry", and so on... 
Yes. I understand. You are right.
But... ;) I like to experiment. 
Yeah. I love to try stupid things!

So, this is no newbie question. I am just a crazy nerd who loves to fiddle. A lot of things got broken by doing this. Yes, thats true. I lost partitions, data, part of my brain ](*,)etc ... well... but i loving to fiddle around! :p


So... here is my question:
Wubi 14.10 cant install on BIOS PCs. Okay. Its dead...
Bugreport: [URL="https://bugs.launchpad.net/wubi/+bug/1385930"]https://bugs.launchpad.net/wubi/+bug/1385930
[/URL]
BUT! Comment #5 (Hakuna_Matata) has an idea how to "fiddle" it. 

It says something like this:
Just exchange some files during installation:
[LIST]
[*]/bin/parted_server (package [http://packages.ubuntu.com/trusty-updates/amd64/ubiquity](http://packages.ubuntu.com/trusty-updates/amd64/ubiquity)) 
[*]lib/x86_64-linux-gnu/libparted.so.0, /lib/x86_64-linux-gnu/libparted.so.0.0.1(package [http://packages.ubuntu.com/trusty/libparted0debian1](http://packages.ubuntu.com/trusty/libparted0debian1)) 
[/LIST]

Wow! Lets get it on! But... How???

[LIST]
[*]How can I exchange files during installation? 
[*]I can reach the terminal and then? 
[*]I downloaded the files to a usb stick and mounted it ... But how can I restart ubiquity? 
[*]Where do I have to copy those files? 
[/LIST]

Again... yes! This is very dangerous to do... but I would like to try...

Maybe there are some gurus around, who could help me?

Thank you!
Greetings from
Ando

---

### Post by Bucky Ball on 2014-11-08
Welcome. Unfortunately Wubi is no longer supported by Canonical or these forums. Please read [HERE]("http://ubuntuforums.org/showthread.php?t=2229766"). Sorry.

*Thread closed.*

If you want help installing a dual-boot, please post a new thread with a descriptive thread title in the appropriate support area. Good luck. ;)

PS: No gurus around, in fact, no one even uses Wubi anymore, pretty much.

---

### Post by Elfy on 2014-11-08
Thread re-opened.

As mentioned Wubi isn't really supported any longer by Canonical.

There are people who'll at least look at wubi threads.

You will be better of looking at a real dual-boot. In the meantime try using a live-session on USB to determine whether you like it, want to try, have hardware that works.

---

### Post by grahammechanical on 2014-11-08
I was going to suggest that you email the person who made comment #5 but he or she did not include a public email address when they registered with Launchpad. I wonder if you missed something. Do you have the problem with installing using Wubi that is mentioned in the bug report? The work around is for that bug. That does not necessarily mean it fixes wubi,

> [COLOR=#333333][FONT=monospace]Try booting from the USB and
going to a terminal (or hit Ctrl+Alt+F1 during the installation) and run:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]sudo parted -l
and
sudo fdisk -l[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]See what errors you get (PS those are lower case L's). If it complains
about GPT data on a MBR formatted disk or returns other errors, then you'll
need to clean them up before the installer will let you continue.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]There's a possibility this is something new but I'd rule the above out
first.[/FONT][/COLOR]


I do not know how to install those packages in a normal install of Ubuntu let alone during installation but this might be a clue: 

> [COLOR=#333333][FONT=monospace](or hit Ctrl+Alt+F1 during the installation)[/FONT][/COLOR]

Could it be as simple as apt-get install <package>?

Regards.

---

### Post by Impavidus on 2014-11-08
That person occasionally visits this forum – at least, I assume it's the same person, given his/her activity in wubi threads: [http://ubuntuforums.org/member.php?u=1134689](http://ubuntuforums.org/member.php?u=1134689)
You could try leaving a message.

---

### Post by hakuna_matata on 2014-11-08
> **anhyb said:**
> 
Wow! Lets get it on! But... How???

[LIST]
[*]How can I exchange files during installation? 
[*]I can reach the terminal and then? 
[*]I downloaded the files to a usb stick and mounted it ... But how can I restart ubiquity? 
[*]Where do I have to copy those files? 
[/LIST]

Again... yes! This is very dangerous to do... but I would like to try...

I patched wubi.exe with 7zip and I copied this version to [a dropbox folder]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na?dl=0"). (wubi1410.exe). 

For [1385930]("https://bugs.launchpad.net/wubi/+bug/1385930") I inserted

[B]data/custom-installation/hooks/early-command.sh
[/B]
```

#!/bin/sh
set -x

architecture=$(uname -m | sed s/i6/i3/)
if [ -f /custom-installation/patch/$architecture/parted_server ]; then
        cp /custom-installation/patch/$architecture/parted_server  /root/usr/bin/parted_server
        cp /custom-installation/patch/$architecture/libparted.so.0.0.1 /root/lib/$architecture-linux-gnu/libparted.so.0.0.1
        ln -s libparted.so.0.0.1 /root/lib/$architecture-linux-gnu/libparted.so.0
fi

```

and 

**data/custom-installation/patch/i386/parted_server** from [http://packages.ubuntu.com/trusty-updates/i386/ubiquity](http://packages.ubuntu.com/trusty-updates/i386/ubiquity) 
**data/custom-installation/patch/i386/libparted.so.0.0.1** from [http://packages.ubuntu.com/trusty/i386/libparted0debian1](http://packages.ubuntu.com/trusty/i386/libparted0debian1) 
**data/custom-installation/patch/x86_64/parted_server** from [http://packages.ubuntu.com/trusty-updates/amd64/ubiquity](http://packages.ubuntu.com/trusty-updates/amd64/ubiquity) 
**data/custom-installation/patch/x86_64/libparted.so.0.0.1** from [http://packages.ubuntu.com/trusty/amd64/libparted0debian1](http://packages.ubuntu.com/trusty/amd64/libparted0debian1)

Additionally, I inserted one line in [B]data/preseed.lupin

[/B]```
**d-i partman/confirm_nooverwrite select continue**
```

to avoid a new ubiquity confirmation dialogue

This workaround is also available on [launchpad.net]("http://bazaar.launchpad.net/~bcbc/wubi/utopic-with-lupin64bit/revision/291?start_revid=291"), Thanks to bcbc for doing this.

**Alternate method under Windows:**

If the Windows part of the installation is finished, you can also replace the file:

[B]ubuntu/install/custom-installation/hooks/early-command.sh

[/B]For 64 bit version add the two files:[B][B][B]

ubuntu/install/[/B]custom-installation/patch/x86_64/parted_server
[/B][/B]**[B][B][B]ubuntu/install/**custom-installation/patch/x86_64/libparted.so.0.0.1

[/B][/B][/B]For 32 bit version add the two files:[B][B][B][B][B][B]

ubuntu/install/[/B]custom-installation/patch/i386/parted_server
[/B][/B]**[B][B][B]ubuntu/install/**custom-installation/patch/i386/libparted.so.0.0.1

[/B][/B][/B][/B][/B][/B]Note: there are also new folders (patch, x86_64, i386)

Finally, you can insert (don't replace it) the line I described above to **[B][B][B][B][B][B]ubuntu/install/**custom-installation/[/B][/B][/B][/B][/B]preseed.lupin[/B]
or confirm "installation on loop2" during installation

---

### Post by anhyb on 2014-11-11
Yeah!

Thank you very very much for all your kindly answers. 

Especially Hakuna_Matata. Yes, you are my guru! :-)
I will try to follow your instructions. 
(And... yes ... I know - Wubi is dead. So: Kids, dont try this at home!!!)
:-)

Thank you!
I will report what happend to me and my PC.

Greetings from
Ando

---

### Post by anhyb on 2014-11-14
Hello everybody.

Yes - we can!\\:D/
I am writing these lines with my new WUBI 14.10 (64bit) Installation.
Thank you Hakuna_matata. Your patched Version just worked like a charm!

Bye!

Greetings from
Ando.

---

### Post by ilianiron on 2015-02-14
Bravo [COLOR=#000000]Hakuna_matata you're the best WUBI-master!I was able to installing 14.10 64-bit without any patching!Alongside with win 8.1 64-bit!Thank's![/COLOR]

---

### Post by Dung_Nguyen on 2015-04-29
after upgrade to ubuntu 15.04 via Software Update, I can't boot with kernel 3.19, only boot work with kernel 3.16[IMG]http://i.imgur.com/brkgxoA.jpg[/IMG]

---

### Post by sudodus on 2015-04-29
The version 15.04 uses systemd instead of init.

Wubi is getting more and more deprecated. New features and methods are used by Ubuntu, and wubi is not developed at all, so it will be more difficult to use it.

---

### Post by hakuna_matata on 2015-05-01
> **Dung_Nguyen said:**
> after upgrade to ubuntu 15.04 via Software Update, I can't boot with kernel 3.19, only boot work with kernel 3.16
For testing purpose, I upgraded Ubuntu 14.10 to Ubuntu 15.04 without any problems but I have inserted in all Wubi versions  [a script]("http://bazaar.launchpad.net/%7Ehakuna-matata/wubi/lp1317437/view/head:/data/custom-installation/patch/loop-remount") for [bug 1317437]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1317437"). 

There is [a fix]("https://code.launchpad.net/~noorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437") written by noorez-kassam but the fix has not been released. So [bug 1317437]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1317437") is still present. If you manually insert the patch of noorez-kassam in Ubuntu 14.10 it is always overwritten by new initramfs packages. So [my script]("http://bazaar.launchpad.net/%7Ehakuna-matata/wubi/lp1317437/view/head:/data/custom-installation/patch/loop-remount") should insert the patch every time if a new package overwrites it. If you use a patched Wubi version from [this dropbox folder]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na?dl=0"), the path of the script is[B] /etc/initramfs-tools/hooks/loop-remount
[/B]
If you don't use the script, you can add it:
```
sudo wget http://bazaar.launchpad.net/~hakuna-matata/wubi/lp1317437/download/head:/loopremount-20150403212347-dqcyn1kotehtxqfj-2/loop-remount -O /etc/initramfs-tools/hooks/loop-remount # download
sudo chmod +x /etc/initramfs-tools/hooks/loop-remount # set mode to executable
sudo /etc/initramfs-tools/hooks/loop-remount # run script
sudo update-initramfs -u -k 3.19.0-15-generic # update initramfs for 3.19.0-15-generic

```
It is also possible to type:
```
sudo update-initramfs -u -k all
```
But in your case, this also overwrites working initramfs for 3.16.


BTW: A patched Wubi version for 15.04 [is available on Launchpad]("https://code.launchpad.net/~hakuna-matata/wubi/upstart"). You can build it with 
```
bzr branch lp:~hakuna-matata/wubi/upstart
cd upstart
make
```
I copied the created wubi.exe to a [dropbox folder]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na?dl=0") (**wubi1504r295.exe). **A second version is also available in this dropbox folder (**wubi1504SB.exe**) with additional support for Xubuntu, Ubuntu GNOME, Ubuntu MATE and SecureBoot.

---

### Post by cartes2 on 2015-10-04
Thanks a lot for this. 
I tried wubi1510r298.exe from your dropbox folder and it's working very well on a win7 dell computer

Thanks a lot for this and hope we will have the same wubi installer for the next lts

---

### Post by Bucky Ball on 2015-10-04
Welcome. As mentioned earlier, Wubi is no longer officially supported and hasn't been for quite some time. Doubtful there will even be a Wubi available on the next LTS (the one you're using isn't standard already). 

Even though Wubi is available, using it is not advisable as you're pretty much on your own when it comes to support and there are few here who know much about it anymore. hakuna_matata seems to be one of those few who will give support for it. Maybe that's changed as this thread hasn't been posted on since May.

Good luck. :)

---

