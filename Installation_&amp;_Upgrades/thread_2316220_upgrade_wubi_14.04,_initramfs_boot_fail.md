---
title: "upgrade wubi 14.04, initramfs boot fail"
date: 2016-03-06
forum: Installation &amp; Upgrades
---

### Post by Xiguus on 2016-03-06
Hi All,
I've just upgraded my wubi precise to 14.04, boot fails at BusyBox with an initramfs prompt. When I exit I get "can't open /root/dev/console: no such file".

There's quite a lot written about this type of error but it seems context-specific and very high risk. Basically I'm looking for confirmation as to the correct procedure for my case. This is my partition table:

```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    34812854    17405403+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    34813952   279007231   122096640    7  HPFS/NTFS/exFAT
/dev/sda3       279009278   976768064   348879393+   f  W95 Ext'd (LBA)
/dev/sda5       279009280   360929279    40960000    7  HPFS/NTFS/exFAT
/dev/sda6       360932418   627177661   133122622   83  Linux
/dev/sda7       627177663   963048554   167935446   83  Linux
/dev/sda8       963048618   976768064     6859723+  82  Linux swap / Solaris
```

The wubi partition is sda5. I can boot to Windows on sda2 and to hosted linux installs on sda6 and sda7.

Output for
```
# dumpe2fs /dev/sda2 | grep superblock
```
is
```

dumpe2fs 1.42.9 (4-Feb-2014)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda2
Couldn't find valid filesystem superblock.

```

and the same for sda3 and sda5. Output for sda6 and sda7 is good.
So:[INDENT]Do I need to repair the filesystem?
What mount command should I use?
[/INDENT]

Thanks in anticipation...
Xiguus

---

### Post by PaulW2U on 2016-03-06
> **Xiguus said:**
> I've just upgraded my wubi precise to 14.04, boot fails at BusyBox with an initramfs prompt. When I exit I get "can't open /root/dev/console: no such file".
WubiI was a great idea but unfortunately it is no longer supported.
See [Forums Staff recommendations on WUBI]("http://ubuntuforums.org/showthread.php?t=2229766") and [WubiGuide]("https://wiki.ubuntu.com/WubiGuide"). It seems that Ubuntu 12.10* was the last Ubuntu release for which Wubi could be expected to work as intended.

You should now install Ubuntu on either a second hard drive or create some space on your existing drive.

* It may have been Ubuntu 13.04 but whatever it is still no longer supported.

---

### Post by lisati on 2016-03-06
It has been a few years since I've used Wubi, and as PaulW2u has pointed out it is not currently supported. 

The last time I used wubi, it used a "virtual" partition contained in a file within the Windows partition, rather than separate partitions as indicated in the fdisk output.

---

### Post by PaulW2U on 2016-03-06
> **lisati said:**
> The last time I used wubi, it used a "virtual" partition contained in a file within the Windows partition, rather than separate partitions as indicated in the fdisk output.
Thanks lisati, I didn't comment on the partitions listed as my last and only use of Wubi was with Ubuntu 10.04 and I couldn't remember how partitions were listed!

[https://bugs.launchpad.net/wubi/+bug/1471344](https://bugs.launchpad.net/wubi/+bug/1471344) shows that Wubi has at long last been removed from the current development release Ubuntu ISOs.

---

### Post by Bucky Ball on 2016-03-06
As mentioned above, Wubi is no longer. Forget and move on. We'd be happy to help you with a dual-boot install but you are not going to have much luck fixing a Wubi install (it hasn't been supported for quite awhile now).

---

### Post by hakuna_matata on 2016-03-06
> **Xiguus said:**
> 
I've just upgraded my wubi precise to 14.04, boot fails at BusyBox with an initramfs prompt.

This is a known issue, see [URL="http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted"]here
[/URL]
After an upgrade it should be still possible to boot into Ubuntu with the old precise kernel from a previous initrd.img.

IMHO there are two possible solutions:

[LIST]
[*]Change the boot option from **ro** to **rw**. If you try this solution I recommend the solution from [German ubuntuusers.de]("https://wiki.ubuntuusers.de/Wubi/Problembehebung/#BusyBox-nach-Start"). The main difference is that it uses **/etc/default/grub **to permanently change the boot option from ro to rw. 
[*]Fix initramfs mounting routine for loop devices like the unreleased patch of Noorez does. see [here]("https://code.launchpad.net/~noorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437/+merge/219927") . I use a script which patches initramfs every time if a new (unpatched) initramfs version is installed. see [here]("http://bazaar.launchpad.net/~hakuna-matata/wubi/lp1317437/revision/292#data/custom-installation/patch/loop-remount") . If you want to install the script, you can use the following commands: 
[/LIST]
```
sudo wget http://bazaar.launchpad.net/~hakuna-matata/wubi/lp1317437/download/head:/loopremount-20150403212347-dqcyn1kotehtxqfj-2/loop-remount -O /etc/initramfs-tools/hooks/loop-remount # download 
sudo chmod +x /etc/initramfs-tools/hooks/loop-remount # set script as executable
sudo /etc/initramfs-tools/hooks/loop-remount # run script
sudo update-initramfs -u # update current initrd.img 

```

---

### Post by hakuna_matata on 2016-03-06
> **Bucky Ball said:**
> We'd be happy to help you with a dual-boot install
Xiguus uses a dual-boot install, too.

> ```

/dev/sda6       360932418   627177661   133122622   83  Linux
/dev/sda7       627177663   963048554   167935446   83  Linux
/dev/sda8       963048618   976768064     6859723+  82  Linux swap / Solaris

```

---

### Post by Bucky Ball on 2016-03-06
So he does. Didn't really read as this thread is about support for an unsupported version of Ubuntu, just reinforced what had already been said, so not much more to add apart from bumping with this post.

Good luck. :)

---

### Post by anhyb on 2016-03-06
Hello everybody,

Maybe (a little) OT... but its time to say "Thank you!"
I am writing this post on ubuntu 16.04 (Beta) using... tada! Wubi!!! (On Windows 7 - 64 Bit).
@hakuna_matata! Your [Wubi16.04(beta)-binaries]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na?dl=0") are working perfect! Thank you for this great work!=d>

Love to see developers who still know the magic (and advantages) of open-source and ... choice!
Ubuntu seems to ignore all this "outsourced" wubi development. What a pity...

Thank you for letting me test the new Ubuntu without touching my Arch- / Windows-Installation nor partitions.
Wubi-System is running nice as all those years before!

Greetings,
Ando

P.S.: Yes, my Wubi-15.10 also worked great all the time before. Every Update: No problems! Running fast and rock-solid.

---

### Post by Bucky Ball on 2016-03-06
Please mark as solved. See the first link in my signature if you don't know how.

---

### Post by Xiguus on 2016-03-07
Hi All, 
Thanks to hakuna_matata for their instructions. 
Here's how it  stands: 
[LIST]
[*] Windows is 7, so issues re Win 8 don't apply. 
[*] Boots previous  kernel, 3.2.0-99 with current (post-upgrade) software direct from GRUB;  obviously some clashes & crashes likely here if this was all we  had, but still good because this has been my 'workhorse' installation  for five years and has all my customisations and configs. 
[*]amend '**linux  /boot/vmlinuz... ro ...**' to '**rw**' boots 14.04, full functionality, very  good (as per above).:D 
[/LIST]
Next step: edit  /usr/share/initramfs-tools/script/local [INDENT]```

ln 146    #mount  ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt}  
+            loopdev=`losetup -f` 
+            losetup=${loopdev}  "host/{$LOOP#/}" 
+            mount ${roflag}  -t ${FSTYPE} ${LOOPFLAGS}  ${loopdev} ${rootmnt} 

``` 
and 
[B]sudo update-initramfs -u

[/B]  
[/INDENT]
I'll hold  off marking this as 'solved' until I've fixed the script, which will  probably be sometime in the next 24 hours; I haven't found any  indications yet that it can break the boot even worse, but I'll dig  around a bit more -- "hasten slowly". 

 Thanks again,
  BR,
 Xiguus

---

### Post by hakuna_matata on 2016-03-07
> **Xiguus said:**
> 
Next step: edit  /usr/share/initramfs-tools/script/local
**/usr/share/initramfs-tools/script_s_/local** is part of package [URL="http://packages.ubuntu.com/search?keywords=initramfs-tools"]initramfs-tools

[/URL]If you edit this file directly, you'll have to repeat this very time after an update of package [initramfs-tools]("http://packages.ubuntu.com/search?keywords=initramfs-tools"). Updates of this packages are not very often, but they happen. So keep in mind.

That's the reason why I use in all versions from [here]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na?dl=0") or newer versions from [here]("https://github.com/hakuna-m/wubiuefi/wiki#releases") a script - as I mentioned in my previous post - which does automatically the job. It replaces
```
mount ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt}
```
with
```
loopdev=`losetup -f`; losetup ${loopdev} "/host/${LOOP#/}"; mount ${roflag} -t ${FSTYPE} ${LOOPFLAGS} ${loopdev} ${rootmnt}
```

It's the code of Noorez. He uses three lines which is more readable, I use only one line because it was easier for me developing the patching script.  

IMHO that's why Ando wrote:
> **anhyb said:**
> 
Every Update: No problems!
@Ando aka anhyb: Thanks a lot for your positive feedback.

---

### Post by Xiguus on 2016-03-08
Thanks hakuna_matata for the tips; sharp to find the path error;).
There is also an error in line +2 of my dummy patch above, ie
```

losetup ${loopdev} "/host/${LOOP#/}'

```
I've done the edit and the upgrade now boots without intervention. Obviously, there's going to be a bit of re-jigging to get all the apps running smoothly again but system works, packages upgrade etc. All very good.:D
Full credit to Noorez Kassam for devisng this solution.
Thanks again,

BR,
Xiguus

---

