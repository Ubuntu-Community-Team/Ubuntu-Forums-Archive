---
title: "Ubuntu AND Kubuntu dual boot - how??"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by T-Stone on 2006-11-29
A few days ago I wiped MS from my laptop and installed Ubuntu. In doing so I partitioned my drives so that I could run another Linux if I wanted to.

hda1 is for Ubuntu
hda5 is for another OS
hda6 is /home

Tonight I installed Kubuntu 6.10 on hda5, and have no option for starting Ubuntu on the grub menu. 

How do I add Ubuntu to the grub menu?

---

### Post by ReaderRat on 2006-11-29
How To Do Most Anything With GRUB
          **[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)**

---

### Post by louieb on 2006-11-29
You probally have two grubs on your system one for Ubuntu one for kUbuntu. 
I am going to guess you are now booting to the grub that was installed by kUbuntu.
If that is so then its just simply add Ubuntu to the current grub install:[LIST]
[*]look in hda1 and see if /boot/grub/menu.lst is still there.
[*]If so look for the Ubuntu entry and copy it.
[*]now go back to hda5 and look for /boot/grub/menu.list.
[*]paste the Ubuntu entry after the Kubuntu entry.[/LIST]That should fix you up for now.
ReaderRats link should take care any questions about viewing or editing the files

---

### Post by T-Stone on 2006-11-29
Sweet! Thanks louieb. That worked. 

Now I wonder what will happen when I have an Ubuntu kernel update.. will it update the Kubuntu grub menu or will I have to do this manual edit each time?

---

### Post by ImmigrantUS on 2006-11-30
? - Why dual boot Ubuntu and KUbuntu if there is a way to try out both DE (KDE & Gnome) either in Ubuntu or Kubuntu -> [http://www.psychocats.net/ubuntu/gnome ]("http://www.psychocats.net/ubuntu/gnome")
 Althou I'm just researching Ubuntu Install and guess there more to it then just DEs differences between them...  
 That leads to next question... 

  ? - Is there really a big difference between Ubuntu and Kubuntu besides DEs? And would installing both DEs into either of them will make us to have the best of both worlds, or it'll have some limitations?

  ? - Finally, why not have both DEs in Ubuntu, making it possible to chose between DEs? 

   Thanks to all!
      Sorry for adding more questions to thread, instead of solutions...
                     Good luck! :confused:

---

### Post by ImmigrantUS on 2006-11-30
? - Why dual boot Ubuntu and KUbuntu if there is a way to try out both DE (KDE & Gnome) either in Ubuntu or Kubuntu -> [http://www.psychocats.net/ubuntu/gnome ]("http://www.psychocats.net/ubuntu/gnome")
 Althou I'm just researching Ubuntu Install and guess there more to it then just DEs differences between them...  
 That leads to next question... 

  ? - Is there really a big difference between Ubuntu and Kubuntu besides DEs? And would installing both DEs into either of them will make us to have the best of both worlds, or it'll have some limitations?

  ? - Finally, why not have both DEs in Ubuntu, making it possible to chose between DEs? 

   Thanks to all!
      Sorry for adding more questions to thread, instead of solutions...
                     Good luck! :confused:

---

### Post by louieb on 2006-11-30
Yea my guess is you will wind up doing a manual change to the grub menu whenever there is kernel update. But it should be just changing the version # on the kernel and initrd entries.
Out of curiosity does Ubuntu and kUbuntu use the same Kernel? My guess is yes.

To: ImmigrantUS
Yes it is possible to use either the Ubuntu desktop (Gnome) or the kUbuntu desktop (KDE) in the same installation. I am set up that way. 
The advantage of that is I can run KDE applications inside Gnome and vise versa. 
The disadvantage is there can be some conflicts in how configuration files are set up. This can lead to things getting a little weird at times.

---

### Post by T-Stone on 2006-11-30
I wanted to do a dual boot because 
a) I didn't want to mess with my Ubuntu
b) I plan to try other linux distros other than just Kubuntu in the future.

---

### Post by Herman on 2006-11-30
Hello T-Stone,
I think that a good way to dual or multiple boot with more than one Gnu/Linux operating system in the same computer , is to use the grub command 'configfile' in the boot entry in the /boot/grub/menu.lst for the other operating system.  If you are not sure, you can add this new boot entry as a seperate one at the bottom of your menu.lst until you test it first, but it will work. This is the method I myself use every day. :D
For example, if you are booting from your Ubuntu menu, add this to it,
```
title        Kubuntu Edgy Eft
savedefault
configfile   (hd0,6)/boot/grub/menu.lst
```(Where: (hd0,6) is the correct partition for your Kubuntu, you may need to replace this with whatever is correct for your particular partition arrangement.)
(You may not really need the 'savedefault' command if it causes problems with other operating systems that don't have the ability to cope with that command. If the 'savedefault' command does cause problems, it can be hashed out or deleted.)
If you want to read more: Operating System Entries for Multiple Booting More Linux Systems............................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

The main advantage of using 'configfile' boot: You will not need to re-edit your menu.lst when the other system has a kernel update.

What the 'configfile' command will do: Brings up your other Grub menu for you to boot from, which will be the one that belongs to the other operating system (Kubuntu in this case), which will be always up to date by it's own automagic kernels list. So, no need to update manually.

Other things you can do: Make each Grub menu have a different color or add a different splashimage, so booting up is more interesting. I have my own splashimage for Ubuntu, and another for Kubuntu.
[COLOR=#666666]To download Ubuntusplash, [Click Here]("http://users.bigpond.net.au/hermanzone/p15/Ubuntusplash.xpm.gz").        Or, for Kubuntusplash, [Click Here.]("http://users.bigpond.net.au/hermanzone/p15/Kubuntusplash.xpm.gz")
Only download if you trust my links, it is a bad habit to be trusting unknown sources, so it is up to you. I am sure they are safe, but it's up to you whether you believe me or not. If not, that's okay, you can make your own splashimages instead if you prefer, here's how, [/COLOR][GO]("http://users.bigpond.net.au/hermanzone/p15.htm#splash")
Attached Thumbnails 
                                         [[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=18428&stc=1&thumb=1&d=1162093549[/IMG]]("http://www.ubuntuforums.org/attachment.php?attachmentid=18428&d=1162093549")  [[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=18429&stc=1&thumb=1&d=1162093549[/IMG]]("http://www.ubuntuforums.org/attachment.php?attachmentid=18429&d=1162093549")


Regards, Herman

---

