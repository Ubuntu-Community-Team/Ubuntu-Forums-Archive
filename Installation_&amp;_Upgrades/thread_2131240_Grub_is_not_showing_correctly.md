---
title: "Grub is not showing correctly"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by ramsubbu on 2013-04-01
I upgraded from 10.04 only a few days back to 12.04.2. I had three OSs at 
this point. 10.04 in two installations and Windows XP. Now after the 
upgrade, I see only two OS ( XP and Ubuntu) in the grub. That too the Linux image 
displayed is that of 10.04 but selecting it takes me to 12.04. I dont 
see the other ( fall-back option) 10.04 installation at all. Please help.

here is the boot-info summary:
[http://paste.ubuntu.com/5621780](http://paste.ubuntu.com/5621780)

Thanks and Regards
Rams.

---

### Post by darkod on 2013-04-01
Grub2 looks OK, I'm just not sure the upgrade was finished correctly. It seems it didn't update the kernel it uses.

Try this, boot the main linux install, at the top of the grub menu. After it loads, open terminal and execute:
```
sudo update-initramfs -u
sudo update-grub
```

Do the command report 3.2.0 kernel as found?

As for the second 10.04 install, you can deal with that later. First the important thing is to update the entry for 12.04 so that it boots the 3.2.0 kernel.

And why do you say you can see the 10.04 install when it's clearly present in /sda8/boot/grub/grub.cfg, you can see the menuentry "Ubuntu 10.04 LTS on /dev/sda5".

---

### Post by Cavsfan on 2013-04-01
Not meaning to butt in here but, after **Darkod** gets you all fixed up you may want to take a look at the link in my signature. 
Your Grub2 menu will only display what you want it to display and it will never have to be messed with again even when new kernels 
are installed on any Ubuntu you have installed. It will always boot into the most recently installed kernel. 
The only time you would need to edit grub is if you delete or install another OS.

By the way, an adimin on here seen I had a swap file for each Ubuntu and told me I only needed one. 
I now have 5 linux systems installed that use the single swap file; even Mint found the swapfile. :)
That will probably require you to edit /etc/fstab on each Ubuntu and put the sdx and UUID of the swap file you want to use.

I have 4 Ubuntus, 1 Linux Mint and 1 Windows 7 Home edition OSs on my PC and here is what my setup looks like:

```
cavsfan@cavsfan-MS-7529:~$ sudo blkid
[sudo] password for cavsfan: 
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" 
/dev/sda2: LABEL="Precise" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" 
/dev/sda3: UUID="2a80f59e-e7c3-418e-aab2-ab5d19255a2f" TYPE="swap" 
/dev/sda5: LABEL="Linux Mint" UUID="b796e378-c9dd-4557-825b-5d5687197609" TYPE="ext4" 
/dev/sda6: LABEL="Quantal" UUID="4d6a25ba-5a4b-4da4-8ae1-9939bc6b6b4c" TYPE="ext4" 
/dev/sda7: LABEL="Raring" UUID="331d2bf4-1749-435a-a218-1c90dee537db" TYPE="ext4" 
/dev/sda8: LABEL="Lucid" UUID="570f351d-6da3-4540-86b6-e12a400f7f44" TYPE="ext4" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs" 

```

Note: The only downfall will be that with Precise and Grub version 1.99 you will see an erroneous error message when you select windows.
But, you can just either wait or press enter and it will go into windows just fine. It does not do this with Grub version 2.00 (Quantal and later).

Labelling the partitions also helps identify them later by name instead of UUID.

This is what I entered for Precise: **sudo tune2fs -L "Precise" /dev/sda2**   If you use double quotes you can have spaces like "Precise Pangolin".
Sometimes this has to be entered a couple of times and sometimes it only takes once to label partitions.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=240838&d=1364840433[/IMG]

---

### Post by ramsubbu on 2013-04-02
Darko, thanks a lot for the guidance. I will try it and post the results.

---

### Post by ramsubbu on 2013-04-02
> **darkod said:**
> Grub2 looks OK, I'm just not sure the upgrade was finished correctly. It seems it didn't update the kernel it uses.

Try this, boot the main linux install, at the top of the grub menu. After it loads, open terminal and execute:
```
sudo update-initramfs -u
sudo update-grub
```

Do the command report 3.2.0 kernel as found?

As for the second 10.04 install, you can deal with that later. First the important thing is to update the entry for 12.04 so that it boots the 3.2.0 kernel.

And why do you say you can see the 10.04 install when it's clearly present in /sda8/boot/grub/grub.cfg, you can see the menuentry "Ubuntu 10.04 LTS on /dev/sda5".

The output of the commands:
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
ramasubramanian@Vostro-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found linux image: /boot/vmlinuz-2.6.32-42-generic
Found initrd image: /boot/initrd.img-2.6.32-42-generic
Found linux image: /boot/vmlinuz-2.6.32-41-generic
Found initrd image: /boot/initrd.img-2.6.32-41-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda2
Found Ubuntu 10.04.4 LTS (10.04) on /dev/sda5
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 192
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done

Yes I see the 3.2 kernel now. but see the error message. How do I fix this
Thanks
Rams.

---

### Post by Cavsfan on 2013-04-02
You are getting an error on line 192 and the only way I know how to tell what line 192 is coming from is to enter 
```
sudo grub-mkconfig --output=grub-mkconfig-output
```
You can call **grub-mkconfig-output** whatever you want. I just named it that for simplification.

The reason I say to output it to a file is that it will probably be too long to see it all in terminal.

That will place **grub-mkconfig-output** in your home directory.
Open that file with gedit or whatever and in preferences put a checkmark by "display line numbers".

Then see what is on or before line 192.

You could post the contents of **grub-mkconfig-output** with CODE around it. That will probably give **darkod** a better idea of what is wrong.

Cheers

---

### Post by darkod on 2013-04-02
Were you editing the /etc/default/grub file or one of the files in /etc/grub.d/ manually? It seems to say there is a syntax error in one of them.

Anyway, the 3.2.0-23 kernel is your 12.04 and it's the main OS, at the top of the list.

---

### Post by ramsubbu on 2013-04-02
But when I rebooted, I get the same grub entries. It doesnt show the 3.2..... But selecting the first entry which shows 2.6.. .. takes me to 12.04. . .I will try the other instructions given here.
I love open source family. thank you guys!

---

### Post by ramsubbu on 2013-04-02
> **Cavsfan said:**
> You are getting an error on line 192 and the only way I know how to tell what line 192 is coming from is to enter 
```
sudo grub-mkconfig --output=grub-mkconfig-output
```
You can call **grub-mkconfig-output** whatever you want. I just named it that for simplification.

The reason I say to output it to a file is that it will probably be too long to see it all in terminal.

That will place **grub-mkconfig-output** in your home directory.
Open that file with gedit or whatever and in preferences put a checkmark by "display line numbers".

Then see what is on or before line 192.

You could post the contents of **grub-mkconfig-output** with CODE around it. That will probably give **darkod** a better idea of what is wrong.

Cheers

These are the lines from 191 to 193.
        search --no-floppy --fs-uuid --set=root 8adbd373-4d9e-4743-916d-2be4347f4d9e
	linux /boot/vmlinuz-2.6.32-40-generic root=UUID=8adbd373-4d9e-4743-916d-2be4347f4d9e ro i8042.reset & i8042.nomux quiet splash
	initrd /boot/initrd.img-2.6.32-40-generic

---

### Post by darkod on 2013-04-03
In the 10.04 on sda5 you seem to be using grub1 with menu.lst. Any particular reason you never upgraded it to grub2?

Now in 12.04 on sda8 when you run update-grub it usually picks up the menu.lst of the other installation and implements it into its grub.cfg. The boot parameters i8042 you are using might not be compatible or correct for grub2. This is just my assumption, I'm not familiar with these parameters. Try temporarily modifying the boot line of 10.04 in sda5/boot/grub/menu.lst and run update-grub in 12.04 again and see if it worked.

I'm not sure why your grub2 would not show the 3.2.0 kernel but it boots you into it. Usually it picks it up by default, unless you did some manual modifications. But that seems to be the smaller problem, because it does boot you into 3.2.0 so you can deal with it later.

---

### Post by ramsubbu on 2013-06-28
Finally, I did the thing I was postponing all the time! Backed up the files and reinstalled ubuntu and xp. Now things are ok :) Thanks for all the help!

---

