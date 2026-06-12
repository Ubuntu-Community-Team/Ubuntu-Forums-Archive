---
title: "No grub after dual booting XP after Ubuntu"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by tom1979 on 2008-09-09
Im sure its been posted many times, but i was actually following a friends instruction on msn this time, now he is offline.

I have ubuntu working fine and windows working fine, but ive lost grub. I can boot into ubuntu with the Super grub cd (by luck i think as i havent a clue what options to use!) and i can choose between a failed xp intall and the proper instal on rebooting without the cd.

Now, ideally id like the failed XP deleted, and the current xp pro and ubuntu on grub.

Previously ive failed miserably unless i install windows first. But this other guy assured me there is a grub fix :)

Auto grub from within windows didnt seem to do anything.

Look forward to some fast help :)

Alternatively if somebody can get my model simulater for windows working in ubuntu, i have xp installed on VM, it would be even more usefull! at the mo it blue screens me... how embarrassing is it to see your ubuntu box blue screen lol.

thanx, tom.

***EDIT***
No grub menu, but now boots into Ubuntu. how can i get the menu and add xp home to it? cheers.

---

### Post by tom1979 on 2008-09-09
Can anyone help with this?!ubuntu still boots, and now i cant boot xp even from the super grab cd... :(

---

### Post by caljohnsmith on 2008-09-09
How about posting your /boot/grub/menu.lst? Also post the output of:
```
sudo fdisk -lu
```
And does Ubuntu have its own partition or did you use Wubi?

---

### Post by tom1979 on 2008-09-09
[http://pastebin.com/mb03d628](http://pastebin.com/mb03d628)

[http://pastebin.com/m2186f9f5](http://pastebin.com/m2186f9f5)

Ive put them in pastebin as i dont know how to stick them in boxes... feel free to cut and paste if you need to to the thread. thanks a lot. tom

Ubuntu was installed first so has first partition, windows was to be on partition 3, after ubuntu and swap, but it failed, then i used another xp cd and it went to partition 4 without asking me to choose partition.

---

### Post by caljohnsmith on 2008-09-09
> **tom1979 said:**
> [http://pastebin.com/mb03d628](http://pastebin.com/mb03d628)

[http://pastebin.com/m2186f9f5](http://pastebin.com/m2186f9f5)

Ive put them in pastebin as i dont know how to stick them in boxes... feel free to cut and paste if you need to to the thread. thanks a lot. tom

Ubuntu was installed first so has first partition, windows was to be on partition 3, after ubuntu and swap, but it failed, then i used another xp cd and it went to partition 4 without asking me to choose partition.
If your Windows is truly on sda4, you might want to consider upgrading its FAT32 file system to NTFS. But anyway, try adding this to your menu.lst to boot Windows:
```
title   Windows
root (hd0,3)
makeactive
chainloader +1
```
That should work if there are no other issues with your Windows (which it sounds like there might be). Also, I would comment the line in your menu.lst that has "hiddenmenu", i.e. make it:
```
#hiddenmenu
```
And also you might want to set your "timeout" in menu.lst to something a little longer than 3 seconds, but it is up to you. Let me know how it goes.

---

### Post by caljohnsmith on 2008-09-09
Geeeez my mistake, Tom. I didn't notice you said you didn't even have Grub on start up any more. When you're in Ubuntu, do the following, and it should put Grub back in your master boot record (MBR):
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
My previous post still applies since you still need to add Windows to your menu.lst. Let me know how it goes. :)

---

### Post by cocokiwi on 2008-09-09
> **tom1979 said:**
> Can anyone help with this?!ubuntu still boots, and now i cant boot xp even from the super grab cd... :(

arg! I have a couple of programs that fix problems with the partitions [www.Paragon.com](www.Paragon.com) have a good one! Burn a DVD ISO and run it on boot..you can run it directly also!cost is not bad ,it can do a lot of different partition work,eg: security deleting drives , including FIXING boot problems,it restores the MBF and can save a copy of the org,if one had problems later! I,ve used it myself with the same problems you are having!I was going to send you the Manual..too big! same with demo! darn it!(grin):lolflag:


A sometime fix.file this one for later.are you getting a error 17 with grub when you boot? if so a fix is simple! for some reason grub will sometmes forget where the files are!???

goto SETUP BIOS...find the drive you are using and go into the list and change AUTO to LARGE..and save bios! there are two different Cyl # listed and switching one or the other depending what was set before it gave that error will fix it!

Regards Dennis:popcorn:

---

### Post by tom1979 on 2008-09-10
> **caljohnsmith said:**
> Geeeez my mistake, Tom. I didn't notice you said you didn't even have Grub on start up any more. When you're in Ubuntu, do the following, and it should put Grub back in your master boot record (MBR):
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
My previous post still applies since you still need to add Windows to your menu.lst. Let me know how it goes. :)


Ok little update, i followed this and i now have grub and windows on the menu and ubuntu is in good order.

Before i did that however i found the windows partitions were empty, so reinstalled xp on partition 3 and ntfs. windows booted then with grub disc. i added a 5gb partition at the end to send windows drivers to, but then windows failed to boot, and now with grub it still fails to boot.

So any ideas please?! cheers for the help so far.

---

### Post by caljohnsmith on 2008-09-10
> **tom1979 said:**
> 
Before i did that however i found the windows partitions were empty, so reinstalled xp on partition 3 and ntfs. windows booted then with grub disc. [COLOR="Blue"]i added a 5gb partition at the end to send windows drivers to, but then windows failed to boot[/COLOR], and now with grub it still fails to boot.

So any ideas please?! cheers for the help so far.
If Windows is now on the 3rd partition, you'll need to change (hd0,3) to (hd0,2) for your Windows entry in your menu.lst. That should fix your Windows entry in Grub, but it sounds like your problem now is Windows related. What is this about a 5 GB partition to "send Windows drivers to"? Also, it would be helpful if you post the new output of:
```
sudo fdisk -lu
```
When you post the results, just highlight them and click the pound sign graphic (#) at the top of the message box to put code tags around them. That's a lot more convenient for us to look at than pastebin I think.

---

### Post by tom1979 on 2008-09-10
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe422995d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   328657769   164328853+  83  Linux
/dev/sda2       328657770   339292799     5317515   82  Linux swap / Solaris
/dev/sda3       339292800   477066239    68886720    7  HPFS/NTFS
/dev/sda4   *   477066240   488392064     5662912+   7  HPFS/NTFS

```

I have a rar file for drivers for my laptop stored on the 5Gb partition, was just to be used as a media swap.

Ah i think i can see the problem already... the forth partition is flagged boot not the third, so how do i correct this? 

Thanks, tom

---

### Post by caljohnsmith on 2008-09-10
> **tom1979 said:**
> ```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe422995d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   328657769   164328853+  83  Linux
/dev/sda2       328657770   339292799     5317515   82  Linux swap / Solaris
/dev/sda3       339292800   477066239    68886720    7  HPFS/NTFS
/dev/sda4   *   477066240   488392064     5662912+   7  HPFS/NTFS

```

I have a rar file for drivers for my laptop stored on the 5Gb partition, was just to be used as a media swap.

Ah i think i can see the problem already... the forth partition is flagged boot not the third, so how do i correct this? 

Thanks, tom
Actually Grub doesn't care which partition is "active", i.e. has the boot flag set; Grub can boot Windows regardless of whether the Windows partition's boot flag is set on. But that's what the "makeactive" line does in Window's entry in menu.lst; it sets the boot flag on for that partition, even though it isn't necessary. It's more of a convention so that you can boot Windows if you ever replace Grub with the Windows MBR. 

So what exactly happens now when you choose Windows from the Grub menu? What errors/behavior do you see?

---

### Post by tom1979 on 2008-09-10
I see the starting ... message followed by random characters i can only read as... ' CODE=pork=pork '

Weird... thats it.

---

### Post by caljohnsmith on 2008-09-10
You said in post #8 that you reinstalled Windows, but then added that 5 GB partition at the end, and after that Windows wouldn't boot. Now that you've done all your repartitioning, I would just reinstall Windows again and it will probably fix the problem; it definitely isn't worth trying to fix Windows if you can just reinstall it again at this point. Let me know how it goes.

---

### Post by jamesxross on 2008-09-11
honestly, i'd just go for a full wipe and reinstall of everything at this point (all these partitions are making my head spin) unless of course you have anything irreplaceable on there, in which case i'd just salvage what i could and then do the full wipe of everything. i like to keep things simple :-P

---

