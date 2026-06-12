---
title: "I messed up boot, how to fix?"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by GARoss on 2010-03-23
I've been working with 10.04 beta as guest OS on VirtuleBox (Mac host) & finally got it working properly. Then decide to share a folder with the host machine. Got that working, too. But, now I cannot boot to 10.04. Somehow, it wants to mount to the shared folder I just setup! I messed something up but don't know what. I can boot to the root desktop. Do I rewrite the GRUB some how?

I'm kinda lost how to check this.

---

### Post by VMC on 2010-03-23
> **GARoss said:**
> I've been working with 10.04 beta as guest OS on VirtuleBox (Mac host) & finally got it working properly. Then decide to share a folder with the host machine. Got that working, too. But, now I cannot boot to 10.04. Somehow, it wants to mount to the shared folder I just setup! I messed something up but don't know what. I can boot to the root desktop. Do I rewrite the GRUB some how?

I'm kinda lost how to check this.

I'm a little lost too. You installed lucid on a virtual box and have been booting it using grub?

Is this a mac machine you have lucid VB installed on?

---

### Post by GARoss on 2010-03-24
> **VMC said:**
> I'm a little lost too. You installed lucid on a virtual box and have been booting it using grub?

Is this a mac machine you have lucid VB installed on?

No, it just boots - no grub menu. I thought I was using the correct terminology but obviously not. Forgive me, I'll try again.

Mac host with Virtual Box 3.1.4. I have WinXP, Kubuntu-64bit & recently, Ubuntu 10.04-64bit beta installed on VB as guest. I had Ubuntu 10.04-64bit running with Guest Additions working but needed to create a shared folder like I did in Kubuntu. This is how I did this in Kubuntu & have no problems with that share. 
[COLOR="Red"]Mac_Share[/COLOR] is shared folder in Ubuntu. [COLOR="Blue"]VM_Mac_Share[/COLOR] is shared folder in Mac.

In the terminal I created a folder-
*mkdir /home/george/Mac_Share* then *gksu gedit /etc/fstab* to edit fstab by adding-
*VB_Mac_Share /home/george/Mac_Share vboxsf rw,uid=1000 0 0* at the bottom of the list. Then- *sudo mount -a* to mount the shared folder. 

The share was working before I quit Ubuntu. The next time I booted I got the errors that I have posted (See jpegs). The 2nd jpeg says it failed to mount */home/george/Mac_Share*. I assume it's trying to boot from there, maybe? Like I said, I'm lost as to what happened!

I must have done something in the terminal to cause this but I can't retrace my steps. I must have accidentally re-written the boot process, maybe? In the 3rd jpeg I can type startx & boot into root. Can I open & edit the boot menu in root?
Need help!

---

### Post by GARoss on 2010-03-24
A person who doesn't know what he's doing can be dangerous!;)

Okay. I booted into *root* by typing *startx*, then deleted out the line in fstab -*VB_Mac_Share /home/george/Mac_Share vboxsf rw,uid=1000 0 0* & saved. Then rebooted without issues to the desktop. So, why would this very same line in Kubuntu work but in Ubuntu 10.04 mess things up? I'm wondering if it could be the superuser status in beta? Here's the id info I get in the terminal -
 
[I]george@george-desktop:~$ id
uid=1000(george) gid=1000(george) groups=4(adm),20(dialout),24(cdrom),46(plugdev),105(lpadmin),115(admin),122(sambashare),1000(george)
george@george-desktop:~$[/I].

I don't get why *VB_Mac_Share /home/george/Mac_Share vboxsf rw,uid=1000 0 0* caused an issue.
Any ideas?

---

### Post by Morbius1 on 2010-03-24
The closest thing I can think of at the moment is a "quirk" in VB when the mount point name on the guest and the shared folder name on the host match. You will get a "protocol error".

Although this is close in this case - it doesn't match exactly:
> *VB_[COLOR=Blue]Mac_Share[/COLOR] /home/george/[COLOR=Blue]Mac_Share[/COLOR] vboxsf rw,uid=1000 0 0*> I'm wondering if it could be the superuser status in betaI don't understand that comment. Does the beta log you in as root?

---

### Post by GARoss on 2010-03-24
> **Morbius1 said:**
> The closest thing I can think of at the moment is a "quirk" in VB when the mount point name on the guest and the shared folder name on the host match. You will get a "protocol error".

Although this is close in this case - it doesn't match exactly:
I don't understand that comment. Does the beta log you in as root?

It refers me as superuser when editing fstab from terminal. (see jpeg 6). I thinks that's different than Kubuntu 9.10.

It was difficult to get Guest Additions up & working ([http://ubuntuforums.org/showthread.php?t=1435210](http://ubuntuforums.org/showthread.php?t=1435210)) but did, finally. The error will be addressed with a VB update, I hope! :)

---

