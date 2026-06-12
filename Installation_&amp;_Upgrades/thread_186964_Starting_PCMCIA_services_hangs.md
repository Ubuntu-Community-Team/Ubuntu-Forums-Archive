---
title: "Starting PCMCIA services hangs"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by juliocesargarcia on 2006-06-02
Hi,

I could not wait to upgrade from breezy to dapper and ran into trouble. Installation using dist-upgrade seemed to go well until it hung starting the PCMCIA services. I have rebooted a couple of times and hangs.

I tired to reboot in recovery mode and the last line is something like this:

[ 18.595889] Intel ISA PCIC probe: not found

and it hangs.

Any clues? Any way to avoid reinstall?

---

### Post by dpm on 2006-06-02
I cannot help much, but I can at least say that there is a bug report related to your problem:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35140](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35140)

Cheers.

---

### Post by juliocesargarcia on 2006-06-02
Thanks! It looks like I'm out of luck and will not be upgrading to dapper on my home system any time soon. If I find the time, I may just do a full intall on my play box. Too bad. Ubuntu had been so easy and reliable up until now.

---

### Post by manemannen on 2006-06-04
Argh - If I only had known this :( Encountered exactly the same thing. Guess I have to do a full install now. Will that work? Du you think the problem is only related to the upgrade or is it just not compatible with my hardware?

---

### Post by diamondsw on 2006-06-04
Argh! Same problem here, but on a Dell PowerEdge server! About the farthest thing from a laptop as you can get. **WHY** on earth is it pulling in a package like that?

I don't know which to be more upset at - the bug, or my lack of trying the dapper flights so I could have found the bug earlier. Thank goodness I made a complete backup before upgrading...

[EDIT: So this has been known for over two months and nothing has been done about it? Why is it only affecting some Breezy upgrades and not others?]

---

### Post by xande on 2006-06-05
I just posted a workaround for this bug to the DapperUpgrade wiki page.  Here's the same post slightly edited for vBulletin formatting.  These instructions are probably not suitable for Aunt Tillie; you need, at least, to know how to boot off of a rescue CD and use the console.  Get help from someone local if you need it.

There is a bug that causes some upgrades to hang on non-PCMCIA machines while setting up the PCMCIA services.  Further, once this happens, the boot process of the machine will always hang at the point of starting PCMCIA services; this happens even when booting in recovery mode.  The bug report is [here]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35140").

The workaround for this bug is as follows (this worked for me; I can make no guarantees about other computers -- USE AT YOUR OWN RISK):

 1. Reboot using a bootable rescue CD.  I recommend the Ubuntu Live CD, [System Rescue CD]("http://sysresccd.org/"), or [Knoppix]("http://www.knopper.net/knoppix/index-en.html").

 2. Mount the partition containing /etc (usually your root filesystem) read-write.  A typical command sequence for this would be
```
mkdir /mnt/hda1
mount /dev/hda1 /mnt/hda1 -o rw
```

 3. Move the files etc/init.d/pcmcia and etc/init.d/pcmciautils somewhere else (to keep them from executing on startup).  A typical command sequence for this would be: ```

cd /mnt/hda1/etc
mv init.d/pcmcia pcmcia.bak
mv init.d/pcmciautils pcmciautils.bak 
```

 4. Remove the CD, and boot your computer from the hard disk.

 5. Before logging in, in the bottom left corner, select Options -> Sessions -> GNOME.  When asked whether to change this to the default session, say "No".  (This step is necessary because the unfinished setup process rendered the default session unusable.)

 6. Open a terminal and run ```
sudo dpkg --configure -a
``` (you can't use synaptic or the updater for this, they're both broken in the current system state).  If you watch the terminal, the attempt to setup the package pcmcia-cs will fail because it can't find the file we moved; this is OK.  Wait for the configure to finish; it will take a long time.

 7. (Optional) Move the pcmcia init scripts back with ```

mv /etc/pcmcia.bak /etc/init.d/pcmcia
mv /etc/pcmciautils.bak /etc/init.d/pcmciautils
```
Now that the setup is finished, they will no longer hang the machine (but if this bug is affecting you, they won't do anything either, so it doesn't matter either way).

 8. Reboot the machine.  It should boot normally now (into Dapper!).  You can now run ```

sudo apt-get -f install
sudo dpkg --configure -a 
```
just to be safe, but they should do nothing.  Congratulations, your system is fixed!

---

### Post by diamondsw on 2006-06-05
So just to be clear, should we move the offending config files out of the way prior to the upgrade, or do we perform these steps after the upgrade crashes? I get the feeling it's the latter since a recovery CD is involved... :(

Is there any way to upgrade without crashing?

---

### Post by juliocesargarcia on 2006-06-05
You will want to make the changes while booted with the liveCD/KnopixCD. There is no other way to do it, I do not think. If your upgrade does not fail, you have nothing to worry about.

I arrived to a similar workaround than the one described before I read the above post. During my experimentation, I tried what xande describes, but some of the desktop packages still tried to start pcmcia and hung (not sure how, and I may be a bit off since I tried a ton of things). In the end, I did something like this:

1. I made a copy of the pcmcia startup script, added and "exit 0" line at the beginning and copied it back to the init.d location

2. Followed the instructions in [http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672), as also described by xande

3. Rebooted

4. started synaptic and noticed that my kernel had not been upgraded. I made sure I had selected the correct linux-image (-k7, in my case). If you have the breezy kernel, you will continue to hang. Not sure why the dist-upgrade did not give me the rigth kernel.

5. restored the init.d/pcmicia script (copied a corrected version to init.d)

I can now reboot and things seem to be mostly OK. The pcmcia service fails at startup, but I may not care because I do not have pcmcia slots in my desktop box.

My problem now is that I cannot login to my box. I get an error about my session lasting less than 10 seconds and .xsession-errors has nothing useful in it. I can start a vnc session, however. Strange ...

---

### Post by manemannen on 2006-06-05
I followed your instructions xande and my system came up as expected. I only had the Nvidia driver issue to attend to but thats another story.

Thanks alot.

---

### Post by diamondsw on 2006-06-05
A few additional tips that may trip people up:
[list][*]If you use autologin, disable it before attempting this. If you don't, I hope you can SSH in from elsewhere and disable autologin and kill X11.
[*]Make sure you update grub or lilo config files to point to the new kernel. Basic advice, yes. Easy to forget, also yes.
[*]Cross your fingers.[/list]

---

