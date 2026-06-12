---
title: "Installing over using Live CD"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by BuntuFreak on 2008-08-10
My Ubuntu is hosed. Upgrade from Gutsy to Hardy got worse day be day and now the system is totally unusable. It boots, I log on, and that's it, can't do anything else. All I see is a glitchy disply of the task bar that does not do anything when I click. Even logging out is a problem.

I wanted to get either the Gutsy or Hardy Live CD and install over my current drive partition - I have XP / Ubuntu dual boot. So I wanted to ask what happens if I pop-in a live CD and ask to install over the Ubuntu partition. Will it format the partition? Because I wouldn't want that. I'm thinking it will simply update the OS directories and fix my machine.

Just to be clear, I have nothing special running like Compiz or any applications like Firefox. My box is simply unusable and I have 80 GB of data I am not in a position to backup right now. So I was thinking of "installing over".

Thanks in advance for any help and clarifications.

---

### Post by Pumalite on 2008-08-10
Install, go Manual and use the old partitions. If you have separate /home; do not format. You can ignore /swap

---

### Post by lukjad on 2008-08-10
Copy over your /home folder to a USB drive or burn it to a CD and then wipe this Gutsy/Hardy mishmash from your computer. Installing a new system is better than upgrading, every time. Then just dump your home folder back into your new system, and *Hey presto!* everything should work. 

One thing though that may cause problems is that when you copy your /home folder, you will also be copying it as root, why will change the permissions. Somehow you will have to change them back. Anyone have any ideas?

---

### Post by SkonesMickLoud on 2008-08-10
You should create a separate /home partition:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You can, and need to do this all from the LiveCD, so you don't need a bootable system.

Installing over WILL delete all of your system files and personal files unless you have said personal files in a separate /home.

If you do lukjad's method:

Ownership problems will be encountered when you try to log in.  So simply press Ctrl+Alt+F1 to get to a virtual terminal, then enter:

```

cd
chmod -R 755 .
chmod 644 .dmrc

```

Don't forget the period after 755.  This changes all permissions back to their defaults.

You may also need to do:

```

chown username:username /home/username

```

These commands may need to be run with sudo.

---

### Post by lukjad on 2008-08-10
Thanks for finishing it off for me. I knew there had to be a way but I never did get along with the chmod command.

---

### Post by BuntuFreak on 2008-08-10
Thanks for responding so quickly folks.

Just needed some clarifications. Will my home directory be wiped out clean or simply overwritten?

The problem is that not only am I not able to boot in XP anymore (i never did it since I got compiz working and its been months :-(). And as I already said, I cannot do anything once I log in to Ubuntu. So backing up to usb drive is not an option.

What happens to "Documents", "Video" etc. folders under my home directory? Will they get wiped out? I have iTunes stuff there don't want to lose.

Thanks much.

---

### Post by Pumalite on 2008-08-10
Use a Live CD and save all your data
Post:
sudo fdisk -lu

---

### Post by SkonesMickLoud on 2008-08-10
> **BuntuFreak said:**
> Thanks for responding so quickly folks.

Just needed some clarifications. Will my home directory be wiped out clean or simply overwritten?

The problem is that not only am I not able to boot in XP anymore (i never did it since I got compiz working and its been months :-(). And as I already said, I cannot do anything once I log in to Ubuntu. So backing up to usb drive is not an option.

What happens to "Documents", "Video" etc. folders under my home directory? Will they get wiped out? I have iTunes stuff there don't want to lose.

Thanks much.

If you create a separate /home partition it will not be over written.  If you do not, it will.

---

### Post by BuntuFreak on 2008-08-11
Thanks guys.

And I believe I can use the boot loader options to boot in "command" node. If so, I'll list the partitions using the command fdisk -lu and hopefully it will also list any usb drives connected. That way I don't even need boot cd for the backup and it might even be faster. Assuming I can do it of course.

I'll try borrow usb drive from a friend today.

Thanks again.

---

