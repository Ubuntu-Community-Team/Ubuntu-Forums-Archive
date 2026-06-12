---
title: "Minimal BASH-like line editing is supported... Error(too many Huffman tables)"
date: 2023-09-04
forum: Installation &amp; Upgrades
---

### Post by kapil07 on 2023-09-04
Today, I encountered the following error upon booting Grub:

                              GNU GRUB version 2.06

  Minimal BASH like line editing is supported.For the first word,TAB lists possible device or file completion.Anywhere else TAB lists possible device or file completions.

 grub>

Instead of being directed towards the usual graphical interface, I was presented with a CLI, asking me for input. I have tried solving the issue with advice given from geeksforgeeks by executing the following commands:

    grub> set root=(hd0,gpt3)
    grub> set prefix=(hd0,gpt3)/boot/grub
    grub> insmod normal
    grub> normal

But after this it throws an error saying `error: jpeg: too many Huffman tables.`

Actually what happened was I was trying to change the background of the gnu grub by gnu customizer app in Ubuntu
[https://paste.ubuntu.com/p/3PFYVXQNqH/](https://paste.ubuntu.com/p/3PFYVXQNqH/)

---

### Post by MAFoElffen on 2023-09-07
> **kapil07 said:**
> Instead of being directed towards the usual graphical interface, I was presented with a CLI, asking me for input. I have tried solving the issue with advice given from But after this it throws an error saying `error: jpeg: too many Huffman tables.`

Actually what happened was I was trying to change the background of the gnu grub by gnu customizer app in Ubuntu
[https://paste.ubuntu.com/p/3PFYVXQNqH/](https://paste.ubuntu.com/p/3PFYVXQNqH/)
Ouch...

You are another victim of 'grub customizer'. Many user's have come here with problems caused by it. I don't know anyone who has really recommended it. (Enough with my disclaimer.)

I do my Grub2 theming by editing the file /etc/default/grub manually. 
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)
[https://www.gnu.org/software/grub/manual/grub/html_node/Theme-file-format.html](https://www.gnu.org/software/grub/manual/grub/html_node/Theme-file-format.html)

Yes, the error you are getting is from picture file that Grub2 cannot rendor in your theming attempt. 

What I would do from there, is to boot from an Ubuntu LiveUSB Installer, mount /dev/sda3 > Make a copy of /etc/default/grub... Edit the file /etc/default/grub, and either comment out the line with the picture file or change it to point to .png file or some other picture file in a format that is supported.

---

### Post by Impavidus on 2023-09-08
> **MAFoElffen said:**
> 
What I would do from there, is to boot from an Ubuntu LiveUSB Installer, mount /dev/sda3 > Make a copy of /etc/default/grub... Edit the file /etc/default/grub, and either comment out the line with the picture file or change it to point to .png file or some other picture file in a format that is supported.

That is to say, edit the /etc/default/grub of the installed system, not the one of the live disk. But you aren't there yet. This will only fix the file from where grub's configuration is sourced, but not /boot/grub/grub.cfg, the file actually used during boot. For that you'll have to run update-grub within a chroot. I don't think I've ever done that myself, but here are instructions: [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

I think the instructions under "Lost password" are good enough (up to and including point 5), otherwise you need those under "Update failure" up to and including point 7. You can skip point 2; just open a terminal window. Then backup your broken grub configuration (just in case you really mess things up), fix the /etc/default/grub and reconfigure grub:```
sudo cp /etc/default/grub /etc/default/grub.bck
sudoedit /etc/default/grub
sudo update-grub
```
I hope I got that right.

I'd stay away from grub customizer. Seeing a pretty picture for three seconds during boot isn't worth the risk of making your computer unbootable.

---

### Post by MAFoElffen on 2023-09-09
Yes. +1 to... you have to update-grub in a chroot... was out the door to go Salmon Fishing. (they are running right now.) LOL

---

