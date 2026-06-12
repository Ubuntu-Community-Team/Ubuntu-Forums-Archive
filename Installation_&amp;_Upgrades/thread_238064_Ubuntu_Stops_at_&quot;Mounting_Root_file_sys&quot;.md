---
title: "Ubuntu Stops at &quot;Mounting Root file sys&quot; after reinstalling grub"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by true_friend on 2006-08-17
HI.
i had lost my mbr last night so reinstalled grub.
i opened terminal in live cd and wrote
sudo su
then grub
then i gave command find /boot/grub/stage1
it returned (hd0.f)
then i gave the command root (hd0,5)
message was it is ext fs partition. i thought ok
then i gave finally setup (hd0)
it wrote all files successfully.
quit exited me and i resarted the system. 
now when i tried to boot ubuntu i said there is no such partion. it is saying that partiton has fat32 file system (which is actually all other partiotion has).
the boot command was /dev/hda8
and in grub it was of cource set to hd0,7
but it was not booting.
i changed the hd0,7 to hd0,5.
it started booting but at "mounting root file system" it stopped booting saying can not mount file system.... some thing such kind.
now tell me what i do in this situtaion.
format my linux partition and reinstall ubuntu???
note: recovery mode has also same problem. 
i spend my hours on configuring linux and when it was ok linux is not booting.
is there any way to recover or i have to destroy my system????
Regards.
True_Friend

---

### Post by true_friend on 2006-08-17
if there is no solution available plz suggest me so i reinstall my linux system.

---

### Post by MetalMusicAddict on 2006-08-17
Is this on a laptop with a docking station or a desktop with a PCI IDE controller?

---

### Post by true_friend on 2006-08-18
it is a desktop computer.
intel 1.8 GHz processor. 
yes it is IDE type controller.
i read it several times in my bios ide master about my hard disk.

---

### Post by MetalMusicAddict on 2006-08-18
The IDE controller is why.

You seem to pretty much have it. I went through the same thing.

If you pull the card you will be able to boot. Its a new thing to Dapper that everyone hates. Dapper enumerates drives in reverse order after boot. Different from install. If you use the desktop cd to see how its labeling them, in you grub menu.list you can change it while in the live cd and then it will boot.

---

### Post by true_friend on 2006-08-18
it was.
hd0,5 in live cd u can see my first post.
but acutally in install its path is hd0,7 in grub and /dev/hda8 in remaining system.
but it boots when i change hd0,7 to hd0,5. 
problem is the other things are set on /dev/hda8 and hd0,7 and the error is can not find root file system.
how to change this path now???

---

### Post by true_friend on 2006-08-18
MetalMusicAddict:
what do u mean by pulling the card???

---

### Post by true_friend on 2006-08-18
i try to change in bootmenue.list

---

### Post by MetalMusicAddict on 2006-08-18
> **true_friend said:**
> MetalMusicAddict:
what do u mean by pulling the card???
I mean physically removing the card.
> **true_friend said:**
> i try to change in bootmenue.list
Changing it in **/boot/grub/menu.lst** should fix it. You might also need to change your fstab for the other drives once you correctly boot.

---

### Post by true_friend on 2006-08-18
thnx a lot. it is done.
i have also written a small how to on it.
i think it is not published yet or may be not of required standard.anyhows it  is a bad situation getting ur system unbootable after reinstalling grub in dapper.

---

### Post by MetalMusicAddict on 2006-08-18
Good to hear you got it sorted out.

Its a MAJOR problem that tons of people hate. Im not even sure if its been fixed/changed.

---

