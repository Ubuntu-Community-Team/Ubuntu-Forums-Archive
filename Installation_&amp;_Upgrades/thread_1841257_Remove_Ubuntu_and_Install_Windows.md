---
title: "Remove Ubuntu and Install Windows"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by Gomezzz82 on 2011-09-09
Hi , sorry if I offend the hardcore Ubuntu users among us but I need help removing Ubuntu from my system and reinstalling Windows 7. I've read many posts but am struggling to understand them, i.e. lots of terminal commands.

I've tried to boot from my Windows CD but get an error message 'Code 5' saying that i can't boot from CD. When I try to install from within Ubuntu using WINE to open the Install.exe, Windows installion opens but when I hit the button for install  I get the error message saying I need at least 700 odd megabites for temporary files. My hard drive is currently partition into two 160gb pieces !! One has Ubuntu and the other formatted as fat32. 

Can anyone give a complete noob some easy to follow instructions on how to remove Ubuntu completely and reinstall Windows 7, your help will be very much appreciated.

Regards

Fabio

---

### Post by BlacqWolf on 2011-09-09
I think error 5 means access denied. Are you sure of where you got your Windows disc from, because this shouldn't be happening. May I ask if at which particular screen do you see the Error 5?

Anyways, you cannot install over Ubuntu through the Windows installer in Wine. Since WINE isn't fully compatible with all apps since the original work is under copyright and so they have to make alternate code with the same effect, so this may cause some compatibility problems. Additionally, Windows will not have the ability to install on a Linux filesystem - Windows 7 only supports NTFS. There's also other serious issues with this.

But, do you happen to have another Windows 7 or Windows Vista disc you can try? Because I don't see how you would get error 5 on an install. My guess is that disc is either corrupt, damaged or counterfeit.

As to installing on the case you don't get the error, just boot your CD/DVD, delete all the Ubuntu partitions (make sure you have all important data on these backed up), select the empty space on the hard drive for use by Windows, and perform your regular install.

---

### Post by Gomezzz82 on 2011-09-09
Hi , thanks for your reply.

I've had to download an ISO image of windows as my laptop didn't come with a copy !! Windows came pre installed and I wish I had checked before deciding to experiment with Ubuntu. 

There error message comes as my Laptop tries to boot from CD, so at startup. 

I'm happy with the process of Instaling Windows if I could get the CD the but its not letting me do that.

I have just tried the CD in a windows machine and I get the same error message , so you were right , the cd is corrupt. I will try burning another one 

regards 

fabio

---

### Post by Mark Phelps on 2011-09-09
Windows 7 does not come on a CD; it comes on a DVD.  So, if what you have is really a CD image, it's not going to work.

You can't install or reinstall Windows OSs using Wine.  That will only allow you to install SOME applications.

Since your PC came with Win7 preinstalled, if your Recovery partition is intact, you should be able to restore from that.  If you're trying that route and it's failing, it could be because the OEM-provided restore program is confused by the presence of a Linux filesystem on the drive.

The Win7 installer SHOULD give you the option to reformat the entire drive, but if it does not, then you need to boot using an Ubuntu desktop CD, open Gnome Partition Editor and remove the Linux partitions from the drive.

---

### Post by recluce on 2011-09-09
> **Gomezzz82 said:**
> Hi , thanks for your reply.

I've had to download an ISO image of windows as my laptop didn't come with a copy !! Windows came pre installed and I wish I had checked before deciding to experiment with Ubuntu. 

There error message comes as my Laptop tries to boot from CD, so at startup. 

I'm happy with the process of Instaling Windows if I could get the CD the but its not letting me do that.

I have just tried the CD in a windows machine and I get the same error message , so you were right , the cd is corrupt. I will try burning another one 

regards 

fabio

Are you really expecting support in installing a pirated copy of Windows? In many jurisdictions, that would be called "aiding and abetting".

Suggestion: try to obtain a recovery CD through the manufacturer of your notebook.

---

### Post by CharlesA on 2011-09-09
> **recluce said:**
> 
Suggestion: try to obtain a recovery CD through the manufacturer of your notebook.

+1. Most laptops come with a recovery partition now adays or prompt you to create recovery dvds.

I've heard that you can download an ISO and install it using the product key that came with your PC, but I wouldn't trust a random ISO found on the internet.

With that, this thread is closed. You are better off asking on a Windows forum.

---

