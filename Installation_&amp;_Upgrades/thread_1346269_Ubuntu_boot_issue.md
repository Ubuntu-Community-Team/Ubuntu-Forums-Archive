---
title: "Ubuntu boot issue"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by Sankou on 2009-12-04
Ok, so here's the situation. I installed Ubuntu via Wubi on a 2nd partition. I know it doesn't make since to use Wubi and then install it to another partition, but thats the only way it would work with my system. An attempt at a fresh install of Ubuntu always crashed. I don't know why. My O/S at the time was winxp 64. I recently upgraded to win7 64. My Ubuntu installation is still on that 2nd partition. I want to be able to boot up to that again, so I'm trying to add it to the boot file in windows. 

So here's the problem, I don't know which file to select to as the 'path' portion in bcdedit. Hell, I don't even know if what I'm trying to do is possible.

If not, would it be possible to make a backup of the disks folder, then do a new Wubi install, and then copy my disks back over?

Hopefully some of that made since. Thanks for looking.

~Sankou

---

### Post by Sankou on 2009-12-04
If anyone else is dual-booting, you may be able to help me. In windows do this:

Start-->Run-->CMD

Then type bcdedit and hit enter.

You should see an ubuntu section, probably at the bottom. What does it say for the 'path' part of this section?

---

### Post by garvinrick4 on 2009-12-04
WUBI uses Windows dos4grub it attaches itself. It does not use grub2 or legacy.

If it is in Windows when you command "bcdedit  you will see it, it says WUBI.

If you installed it on its own partition with WUBI who knows what and where the boot
would go. What did you do partition and then install in different times? Did you make
the partition manually Where is the partition for D: that linux sees as VIsta in windows 7. sda3 or sda4
boot is sda1  and 7 in sda2.    
  Did you make an extended partition like sda3 or4 to put sda5 and sda6 your linux and swap
partition and then stick wubi in there somehow.  

Look at gparted and see what it looks like. If it is a mess better off just doing a clean install 
in 7 at the boot. It has an image in the one linux calls Vista.

---

### Post by u.b.u.n.t.u on 2009-12-04
You have a HDD with Windows 7 installed, a partition with Ubuntu 9.10 installed. Is this correct?

Are you having an issue with the boot loader? Ubuntu 9.10 should have sorted that with the initial install.

---

### Post by u.b.u.n.t.u on 2009-12-04
> **garvinrick4 said:**
> Look at gparted and see what it looks like. If it is a mess better off just doing a clean install 
in 7 at the boot.

Sankou, that would probably be the best way forward, unless you like a potential challenge!

---

### Post by Sankou on 2009-12-04
Ok, to clarify. I had windows xp installed on drive C:. When i installed ubuntu with wubi, I put the disks and all that on an extended partition D:. I formated 'C' when i installed windows 7. 'D' was not changed at all. That means my root.disk is still there and unchanged. I just want to be able to boot to it again. Can I make a backup of it, then install ubuntu with wubi - using the same settings as before, and then replace the new root.disk with my backup? Would something like that work? I just dont want to lose my settings and files....

---

### Post by u.b.u.n.t.u on 2009-12-04
You had a HDD with XP.

Then you had a HDD with XP and a partition with Ubuntu.

Now you have a HDD with Windows 7 and a partition with Ubuntu.

You can boot into Windows 7, but cannot boot to Ubuntu 9.10. Is that correct?

If correct, then the solution is to update the Windows 7 boot loader to add Ubuntu 9.10.

---

### Post by misterbk on 2009-12-04
Sankou, I'm on Win7 and about to finish doing exactly what you are trying to do.  One more boot and I should be there.

You'll want to google up a tool called "EasyBCD" made by NeoSmart.  It's a front-end to edit the windows 7 boot configuration, basically what BCDEdit does, except without all the worry of mistyping something and hosing your system.

Attached a screenshot.

I'll let you know if it works.

---

### Post by Sankou on 2009-12-04
> **u.b.u.n.t.u said:**
> You had a HDD with XP.

Then you had a HDD with XP and a partition with Ubuntu.

Now you have a HDD with Windows 7 and a partition with Ubuntu.

You can boot into Windows 7, but cannot boot to Ubuntu 9.10. Is that correct?

If correct, then the solution is to update the Windows 7 boot loader to add Ubuntu 9.10.

Yea, that's right. But does it make a difference that the partition with Ubuntu was installed via Wubi?

And if I can just add Ubuntu to the boot loader, how would I go about that? I tried bcdedit and it didn't work.

---

### Post by Sankou on 2009-12-04
> **misterbk said:**
> Sankou, I'm on Win7 and about to finish doing exactly what you are trying to do.  One more boot and I should be there.

You'll want to google up a tool called "EasyBCD" made by NeoSmart.  It's a front-end to edit the windows 7 boot configuration, basically what BCDEdit does, except without all the worry of mistyping something and hosing your system.

Attached a screenshot.

I'll let you know if it works.

I tried that earlier, I couldn't make it work. I think it has something to do with the fact that its a Wubi install. Idk. The problem was the file that it links to in the 'path' section. Then I tried to manually change that file with bcdedit, I couldn't find the right file...

---

### Post by u.b.u.n.t.u on 2009-12-04
Windows 7 is working and booting correctly.

Perhaps it would be best to simply reinstall Ubuntu 9.10? Is that an option?

UPDATE

You had a working XP and Ubuntu, if I understand correctly, and by installing Windows 7 you basically created a situation like installing Windows on Linux, eg rather difficult to resolve.

---

### Post by misterbk on 2009-12-04
Yeah, I just tried it on my system and it didn't work either.

I used to do this all the time on XP...  Haven't had much time to troubleshoot so far so I'll see what Google digs up.

---

### Post by Sankou on 2009-12-04
I just tried this-

bcdedit /set {64e5944a-d941-11de-b036-b0712ecfeecb} path \ubuntu\winboot\wubildr.mbr

It tries to boot up, but I get some weird error about a kenrnal missing or something.

I think I'm going to try reinstalling Ubuntu with Wubi and replacing the new .disk file with my back up root.disk. Or maybe even the whole disks folder.

If that doesn't work, I guess I'll just have to do a new ubuntu install. I really hate to lose months of work and files, but I might not have a choice.

---

### Post by u.b.u.n.t.u on 2009-12-05
> **Sankou said:**
> . I really hate to lose months of work and files, but I might not have a choice.

As you have "months of work" on the line I think we should continue to try and resolve this.

Please don't do anything yet.

---

### Post by Sankou on 2009-12-05
> **u.b.u.n.t.u said:**
> As you have "months of work" on the line I think we should continue to try and resolve this.

Please don't do anything yet.

Yea, I haven't yet. Still researching on google and yahoo. And thanks everyone for all the input and help so far =)

---

### Post by u.b.u.n.t.u on 2009-12-05
> **Sankou said:**
> 

You should see an ubuntu section, probably at the bottom. What does it say for the 'path' part of this section?

[IMG]http://img31.imageshack.us/img31/2325/20091205162356.png[/IMG]

I think that the identifier is what is needed as such would act as a key. A way to discover or recreate the identifier.

---

### Post by u.b.u.n.t.u on 2009-12-05
This needs a new post. 

There are a number of avenues to explore at the following page and I have cited one that may be of interest.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)



"**How can I access my Wubi install and repair my install if it won't boot?**

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.

To check the filesystem you can use:

sudo fsck /win/ubuntu/disks/root.disk"




Another possible area to explore.


[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)


"Introduction

The Loopmounted Virtual Partition Manager allows users to upgrade their existing Wubi or Lubi installation to a standard Ubuntu system by transferring all data, settings, and applications from the original install to a dedicated partition. The advantages of upgrading using LVPM are better disk performance and reliability, and the ability to replace the original operating system with Ubuntu."

---

### Post by Sankou on 2009-12-05
Very useful links, I think I may have found a solution.

---

### Post by u.b.u.n.t.u on 2009-12-05
> **Sankou said:**
> Very useful links, I think I may have found a solution.

I think you are taking point, writing the "how to" manual for this topic! ;)

---

### Post by garvinrick4 on 2009-12-05
If you do not find a way just delete wubi in windows grub.

bcdedit /delete { identifier # }      brackets need to be in code.

uninstall all aspects of wubi in windows Ubuntu folder and
reinstall.  Put disk in tray pick WUBI tell size, tell password 
and go.  Wait 12 minutes and start putting your system together.

---

### Post by misterbk on 2009-12-05
Here's a thought...  Could you first make a copy of your Ubuntu folder, then do a fresh Wubi install to rebuild the correct boot options, and then replace the new Ubuntu folder with your backup?

---

### Post by u.b.u.n.t.u on 2009-12-05
> **misterbk said:**
> Here's a thought...  Could you first make a copy of your Ubuntu folder, then do a fresh Wubi install to rebuild the correct boot options, and then replace the new Ubuntu folder with your backup?

I suspect that the key to unlocking this problem is the identifier, which I suspect is a key to unlocking the wubi install of Ubuntu. ;)

So how to find this unique rather long alphanumeric key, bypass it, or recreate it, are questions that need an answer.

We know where the wubi Ubuntu install is. The problem is gaining access to it.

When Windows 7 was installed over XP it destroyed the boot loader and therefore the key.

If Sankou can solve this with our participation then it would be quite an achievement I would think.

A wubi developer would know the answer easily and at the end of the day, that may well be the last resort to get it sorted.

Certainly interesting.

---

### Post by Sankou on 2009-12-05
Solved! I'm posting from my Ubuntu right now. Here's what I did:

I went to the link provided by u.b.u.n.t.u and it led me to a place to download previous versions of Wubi. The version of ubuntu I originally installed was 9.04, so I downloaded that version of Wubi. I installed it using the exact same settings as my original install. After installing it I rebooted my computer and went through the setup process and rebooted again. I then logged on once and rebooted the computer. I booted up to windows 7 and replaced the new "disks" folder with the one from my backup. After that I rebooted and everything worked perfectly!

That was probably the hard way to do things, but it worked! Thanks for the help everyone!

~Sankou
__

---

### Post by u.b.u.n.t.u on 2009-12-05
> **Sankou said:**
> Solved! I'm posting from my Ubuntu right now. Here's what I did:

I went to the link provided by u.b.u.n.t.u and it led me to a place to download previous versions of Wubi. The version of ubuntu I originally installed was 9.04, so I downloaded that version of Wubi. I installed it using the exact same settings as my original install. After installing it I rebooted my computer and went through the setup process and rebooted again. I then logged on once and rebooted the computer. I booted up to windows 7 and replaced the new "disks" folder with the one from my backup. After that I rebooted and everything worked perfectly!

That was probably the hard way to do things, but it worked! Thanks for the help everyone!

~Sankou
__

Fantastic news! Bravo!!!

Please enlighten me to what role if any the "indentifer" had.

Also please do consider creating your own Ubuntu wiki page "how to" and create a signature linking to that.

I do think others would find such of significant assistance.

As a guide my wiki page is in my signature.

[IMG]http://img207.imageshack.us/img207/2553/thcheers.gif[/IMG]

---

