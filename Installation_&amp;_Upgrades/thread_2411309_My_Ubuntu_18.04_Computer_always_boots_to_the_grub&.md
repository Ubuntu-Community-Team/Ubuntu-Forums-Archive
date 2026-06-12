---
title: "My Ubuntu 18.04 Computer always boots to the grub&gt; prompt"
date: 2019-01-28
forum: Installation &amp; Upgrades
---

### Post by DZDB on 2019-01-28
I have a fresh Ubuntu 18.04 install.  I just upgraded from Ubuntu 16.04.  Now my computer is always booting to the grub> prompt.   The screen looks as follows:

GNU GRUB version 2.02 beta2-9

Minimal BASH-like line editing is supported. For the first word, TAB list possible command completions.  Anywhere else TAB lists possible device or file completions.  ESC at any time exists.

I performed the following commands at the grub prompt> and I successfully booted to Ubuntu 18.04 screen.

grub> set root=(hd0,4)
grub> linux /boot/vmlinuz-4.2.0-16-generic root=dev/sda4
grub> initrd /boot/initrd.img-4.2.0-16-generic
grub> boot

Once again, I then successfully boot to the Ubuntu 18.04 screen.  However when I restart the computer it will again boot to the grub> prompt, which is my issue.

I have been reading some of the Grub prompt cases.  One person had the following resolution:

"If booting is successful now, you can get your uuid (not partuuid) by typing blkid and verify that the correct one is noted in /boot/EFI/Ubuntu/grub.cfg."

I believe the above stated resolution will work for me.  However I did not completely understand the resolution.

My questions are as follows:
1) Do I type blkid in the terminal? If not then what "exactly" do I type?
2) How do I verify that the correct one is noted in /boot/EFI/Ubuntu/grub.cfg? I am a novice and I need more detailed instructions.

I am hoping someone can answer my questions.

---

### Post by Autodave on 2019-01-28
Did you upgrade from one to another or did you wipe out the old install and put a new install in?

---

### Post by DZDB on 2019-01-28
I wiped out the old install and put a new install in.

---

### Post by CatKiller on 2019-01-28
> **DZDB said:**
> My questions are as follows:
1) Do I type blkid in the terminal? If not then what "exactly" do I type?

Yes, but as root.

>  2) How do I verify that the correct one is noted in /boot/EFI/Ubuntu/grub.cfg? I am a novice and I need more detailed instructions.

I am hoping someone can answer my questions.

The file itself is tiny. You won't have any trouble identifying the entry.

However, your path is incorrect. It should be **/boot/efi/EFI/ubuntu/grub.cfg**.

Tab-completion won't work for the EFI partition if you're a normal user, so you might as well be root for all of this to save yourself from more typos.

```

sudo -i
blkid

```
You'll be looking for the UUID of your / partition. UUIDs are a really long string of characters. Check that that matches the one that GRUB is looking for:

```

cat /boot/efi/EFI/ubuntu/grub.cfg

```

If it's not the same, edit that file to correct it:

```

nano /boot/efi/EFI/ubuntu/grub.cfg

```

So, the results when I do those are:

```

blkid 
/dev/nvme0n1p1: UUID="7EC4-2B60" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="94069844-9d6a-4a92-bdfd-163782b30889"
/dev/nvme0n1p2: UUID="**80ecc774-f0d7-4325-b0e9-81c79eed3ead**" TYPE="ext4" PARTUUID="363fc6ac-56bc-4466-a0d0-68fd408f9acb"
/dev/nvme0n1: PTUUID="dd6526eb-5a85-40c2-9976-800baf5cb0c3" PTTYPE="gpt"

cat /boot/efi/EFI/ubuntu/grub.cfg 
search.fs_uuid **80ecc774-f0d7-4325-b0e9-81c79eed3ead** root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

It's possible that you'll need to also change your configuration elsewhere so that the incorrect value doesn't get written there again on the next update-grub, but I could be wrong on that.

---

### Post by DZDB on 2019-01-30
Hi Cat,

 I typed the following code in the terminal:

cat /boot/efi/EFI/Ubuntu/grub.cfg

I received the following message:

"No such file or directory"

When I typed the following code:

nano /boot/efi/EFI/Ubuntu/grub.cfg

I received the following message:

"[Directory '/boot/efi/EFI/ubuntu' does not exist"

What is my next step? Is there another Ubuntu 18.04 LTS  iso file that I can use?

---

### Post by CatKiller on 2019-01-30
That's what the sudo -i is for. Normal users can't peek at the EFI stuff. That's why tab-completion doesn't work, either.

Do all of those bits as root, using tab-completion, and then use logout to stop being root.

---

### Post by DZDB on 2019-02-02
To CatKiller or anyone who can help me:

I believe that I did input all bits (i.e. "blkid" and "cat /boot/&#8230;") in the terminal at the root level.  Please note that the "blkid" command ran properly.  Unfortunately the [LEFT][COLOR=#222222][FONT=Verdana]"cat /boot/&#8230;" command did not run properly.  [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]Please see my output below:[/FONT][/COLOR][/LEFT]

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
jyoti@jyoti-All-Series:~$ sudo -i
[sudo] password for jyoti: 
root@jyoti-All-Series:~# blkid
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/sda1: UUID="9C5E-2D6B" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="ff884250-0c97-4b23-a5cb-de5273a4e65a"
/dev/sda2: PARTUUID="ccc1e37e-bac7-4f77-853a-47f8235b5533"
/dev/sda3: UUID="654be3c9-342c-4ab8-979a-52f12f95413f" TYPE="swap" PARTUUID="609c8492-ca2e-4809-934a-726c1484acdc"
/dev/sda4: UUID="213a7f72-f62e-4a7b-a1c0-4a9b18e551c4" TYPE="ext4" PARTUUID="ae34d31d-f449-41ae-b6ff-50b393bc6bf4"
/dev/sdb1: LABEL="USB DISK" UUID="6E2E-53BD" TYPE="vfat" PARTUUID="6ed9c701-01"
root@jyoti-All-Series:~# cat /boot/efi/EFI/ubuntu/grub.cfg
cat: /boot/efi/EFI/ubuntu/grub.cfg: No such file or directory
root@jyoti-All-Series:~# sudo -i
root@jyoti-All-Series:~# cat /boot/efi/EFI/ubuntu/grub.cfg
cat: /boot/efi/EFI/ubuntu/grub.cfg: No such file or directory
root@jyoti-All-Series:~# 



 

 

Did I run all Terminal commands at the root level? If so then what is my next step?

---

### Post by CatKiller on 2019-02-02
Use Tab-completion to make sure you're using the correct path: it's possible your path is different to mine for some reason. It doesn't work as a normal user in this case, but it will work as root. It's also a good habit to get into, generally. 

Type the first letter or two of each bit and then press Tab. The shell will then complete as much as it can. If there's more than one way to complete it the computer will beep if you have a bell set up, but it won't complete. Pressing Tab twice at that point will list all the ways that it could be completed, so you can then type enough extra letters to enable it to autocomplete.

You can also use the other standard commands like cd and ls to identify the location of the grub.cfg in your EFI.

Of course, if you don't have a grub.cfg in your EFI at all, that would explain why you have to configure grub each time at boot.

---

### Post by DZDB on 2019-02-03
To Catkiller or anyone who can help me:

On the "cat /boot/&#8230;" command in the terminal, I tried typing the first two letters (i.e. ca) and then I pressed the [Tab] key.  I got no results.  I then pressed the [Tab] key again.  At that point I guess I got my various options.   I then typed one of those options (i.e. [LEFT][COLOR=#222222][FONT=Verdana]canberra-gtk-play) and the [Tab] key.  Again I got no results.[/FONT][/COLOR][/LEFT]  Please see my output below:


jyoti@jyoti-All-Series:~$ sudo -i
[sudo] password for jyoti: 
Sorry, try again.
[sudo] password for jyoti: 
root@jyoti-All-Series:~# blkid
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/sda1: UUID="9C5E-2D6B" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="ff884250-0c97-4b23-a5cb-de5273a4e65a"
/dev/sda3: UUID="654be3c9-342c-4ab8-979a-52f12f95413f" TYPE="swap" PARTUUID="609c8492-ca2e-4809-934a-726c1484acdc"
/dev/sda4: UUID="213a7f72-f62e-4a7b-a1c0-4a9b18e551c4" TYPE="ext4" PARTUUID="ae34d31d-f449-41ae-b6ff-50b393bc6bf4"
/dev/loop7: TYPE="squashfs"
/dev/sda2: PARTUUID="ccc1e37e-bac7-4f77-853a-47f8235b5533"
/dev/sdb1: LABEL="USB DISK" UUID="6E2E-53BD" TYPE="vfat" PARTUUID="6ed9c701-01"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
root@jyoti-All-Series:~# ca
cal                caller             capsh              cat                cautious-launcher
calendar           canberra-gtk-play  captoinfo          catchsegv          
calibrate_ppa      cancel             case               catman             
root@jyoti-All-Series:~# canberra-gtk-play


I am somewhat familiar with the command "ls".  I used the ls command to identify where I need to set the root.  Please see example below:

grub> set root=(hd0,4)

However I am not sure how to use the ls command to get my computer to boot to Ubuntu's 18.04 Desktop screen as opposed to the grub prompt (i.e. grub>).

---

### Post by oldfred on 2019-02-03
It may just be easier to use Ubuntu live installer and add Boot-Repair.
From Boot-Repair use the advanced options and total reinstall of grub.
Usualy the suggested auto fix works, but best to have someone review that first, it not using advanced mode of Boot-Repair.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Shows advanced options screens.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by CatKiller on 2019-02-03
> **DZDB said:**
> On the "cat /boot/&#8230;" command in the terminal, I tried typing the first two letters (i.e. ca) and then I pressed the [Tab] key.  I got no results.  I then pressed the [Tab] key again.  At that point I guess I got my various options.   I then typed one of those options (i.e. canberra-gtk-play) and the [Tab] key.  Again I got no results.
 
cat is cat. You want that command. It's the path that you need to establish. I have no idea what canberra is, or why you'd choose to use it now.

To use tab completion, you'd do (as root in this case) cat /bo<Tab>e<Tab>E<Tab>u<Tab>g<Tab>.cfg. That would complete the path, if the file is actually in that place. If any of those Tab-completions don't complete, pressing Tab twice will show you what's available at that point.

To use cd and ls to identify the correct path, you would do 
```
cd /boot
ls
```

Then, if the output shows "efi" you'd do

```
cd efi
ls
```

and so on until you'd identified the grub.cfg that's in your EFI. cd changes directory. ls lists the contents of the directory you're in. cat puts the contents of a file on the screen.

In particular, you keep randomly capitalising Ubuntu in the path in your posts here. Case is important. We need to know if you're putting a typo into the path you're using, or if the file exists but is in a different place, or if the file doesn't exist at all. If the file exists and has the incorrect information in, that's one fix. If the file doesn't exist at all, that's a different one.

Use code tags when you're posting terminal output here. It makes it much easier to read.

> However I am not sure how to use the ls command to get my computer to  boot to Ubuntu's 18.04 Desktop screen as opposed to the grub prompt  (i.e. grub>).

You already know how to make it boot: it can't find the next stage until you tell it where to look. As soon as you do that, it boots fine. This part is telling it the right place to look from the start.

---

### Post by DZDB on 2019-02-26
I got really busy.  Now I am coming back to my issue.  After oldfred's post, I performed the following actions:

1) I started my computer and it booted to the grub > prompt.

2) [LEFT][COLOR=#000000][FONT=Ubuntubeta]I performed the following commands at the grub prompt> [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]grub> set root=(hd0,4)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]grub> linux /boot/vmlinuz-4.2.0-16-generic root=dev/sda4[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]grub> initrd /boot/initrd.img-4.2.0-16-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]grub> boot

This got me to the Ubuntu 18.04 desktop screen.


3) I went into the terminal and I typed the following:

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair


The above commands enabled me to successfully install the Boot Repair application.


4) I then launched Boot-Repair by typing (without the quotes) "boot-repair" in the terminal.

5) I then clicked on "Recommended repair (repairs most frequent problems)".

6) This performed a scanning action.  I then received the following error message:

    "Please use this software in a live-session (live-CD or live-USB).  This will enable this feature.  Operation Aborted."


Obvioulsy I am a beginner.  I do not know what it means by "using this software in a live-session (I would use live-USB)".  


Can someone please help me?


[/FONT][/COLOR][/LEFT]

---

### Post by oldfred on 2019-02-26
Some functions can only be done on unmounted systems, so you can use the Ubuntu live installer, your flash drive or DVD in live mode and add Boot-Repair to it.
You can run the report from your installed system.

you can from your system try just the re-install of grub.
       sudo grub-install /dev/sda
sudo update-grub

If UEFI entries need to be updated, there are mulitple other grub install commands.

---

### Post by DZDB on 2019-12-05
**[SIZE=5]SOLVED[SIZE=1][/SIZE][/SIZE]**

I solved my problem by doing a reinstall.  

During the installation process, when I got to the "Installation type" screen, I chose the following option:

Erase disk and Install Ubuntu 18.04*[COLOR=#ff0000][/COLOR]*
[COLOR=#ff0000]Warning:[/COLOR] This will delete all your programs, documents, photos, music and other files in all operating systems.

Before I was choosing an option that read as follows (this may not be verbatim):
Erase Ubuntu 18.04 and reinstall Ubuntu 18.04


Please note that I am a newby.  So I could never understand the suggestions to adjust the commands in the root directory. For a newby like me, it was best to just wipe out the hard disk and start clean.  This was actually my mom's computer.  The only thing she really needs is a browser so that she can surf the internet, watch YouTube videos and read her emails.  Therefore erasing the disk and reinstalling Ubuntu 18.04 was not a very time consuming process.

I want to give many thanks to everyone who tried to assist me.

---

