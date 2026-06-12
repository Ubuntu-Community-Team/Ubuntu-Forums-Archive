---
title: "Grub Customizer"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by rocky289 on 2012-10-24
Hi
 
To get familiar with some of the latest distros I have installed Zorin os 6, Linux 13 Mint, Linux 13 Cinimon, Lubuntu 12.4 & Ubuntu 12.4 on 1 pc.
The are multi booted & all run happily together.
I have installed Grub Customizer on Ubuntu 12.4 to groom the grub, but it dosent seem to do any thing.
I am firstly trying to change the order in the list.
Secondly would like to edit the entry for Lubuntu which shows up as a second entry for Ubuntu.
The only way I can tell them apart is by the /sda number.
 
Any help would be appreciated.

---

### Post by Herman on 2012-10-24
For setting user friendly titles for your other flavors of Ubuntu, you're welcome to try this little how-to and see if it still works, [How to Have All Your OS Hostnames in your GRUB Menus.]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20OS%20Hostnames.html")
I have tested it myself and it worked fine at the time but that was a while ago and software changes frequently.

Regards, Herman :)

---

### Post by Bucky Ball on 2012-10-24
I'm wondering if you're dealing with the right grub. Might be a silly question, but are you sure 12.04 is running the show? I got confused with this when I had three *buntu installs. I could see how I could easily get confused with your setup! 

If you update the grub on one install then you need to boot into the install that's in control at boot, if you follow me, and update that grub so it can pick up the changes of the updated grub from the other install. This is the thing. If you get a kernel update in Lubuntu, say, that won't be reflected in your selections at boot until you update the grub in the install that is in control at boot ...

Anyhow, you sure you have GCustomizer installed in the correct OS? Have you tried updating grub in any of the other installs, if they use it? This might help identify the fat controller ...

---

### Post by rocky289 on 2012-10-24
> **Herman said:**
> For setting user friendly titles for your other flavors of Ubuntu, you're welcome to try this little how-to and see if it still works, [How to Have All Your OS Hostnames in your GRUB Menus.]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20OS%20Hostnames.html")
I have tested it myself and it worked fine at the time but that was a while ago and software changes frequently.

Regards, Herman :)

Thank you Herman

That sounds like it would work but I'm not confident enough at this stage to attempt that.
I would probably run off the rails before I got to the end of the line.

---

### Post by rocky289 on 2012-10-24
> **Bucky Ball said:**
> I'm wondering if you're dealing with the right grub. Might be a silly question, but are you sure 12.04 is running the show? I got confused with this when I had three *buntu installs. I could see how I could easily get confused with your setup! 

If you update the grub on one install then you need to boot into the install that's in control at boot, if you follow me, and update that grub so it can pick up the changes of the updated grub from the other install. This is the thing. If you get a kernel update in Lubuntu, say, that won't be reflected in your selections at boot until you update the grub in the install that is in control at boot ...

Anyhow, you sure you have GCustomizer installed in the correct OS? Have you tried updating grub in any of the other installs, if they use it? This might help identify the fat controller ...

I am thinking you are on  the right track here. 
I didn't really  take note of the order I did things.
I chose Ubuntu as it is more the base OS & I wasn't sure if the Grub Customizer was compatible with the others.
So, from your last sentence, how could I tell which is the fat controller?

---

### Post by Bucky Ball on 2012-10-24
I guess first you would figure out which OSs use grub, then try and figure which of them you installed last. Unless you manually instructed the install to put it elsewhere, it would have written to the MBR on sda and that would be the one. Which OS is at the top of the list at boot? That might be a clue ...

---

### Post by grahammechanical on 2012-10-24
The last Linux OS to be installed puts it own version of Grub into the MBR of the hard disk.

You need to chose an OS to be your base OS (in this case Ubuntu) and install Grub customizer in to that. Then after you have made your changes using Grub Customizer you not only save the changes (which will write a new Grub configuration file for that OS) but you must use the file menu of Grub Customizer to save to MBR. Then the Grub menu for that OS (Ubuntu) will be in charge.

Now, whenever one of the other OSes updates a kernel or especially if it updates Grub you simply boot into Ubuntu and run Grub Customizer again and save to MBR again.

There is something that you should know about. Ubuntu 12.04 uses Grub 1.99. whereas 12.10 uses Grub 2.0. Grub customizer does not work as well with Grub 2.0 configuration files. The Grub menu is still usable but you will not get the sub-menus that Grub 2.0 now gives us.

I have tried using Grub customizer on 12.10 but I have not tried it on 12.04 since installing 12.10. Grub 2.0 will come into 12.04 at the end of January.

Regards.

---

### Post by oldfred on 2012-10-24
With multiple systems or multiple drives I suggest running bootinfoscript. You document system and see what is installed where. I run it as part of my rsync backup just to have a current copy of results.txt in my backup.

I often now suggest Boot-Repair's BootInfo as it runs the bootinfoscript and adds info.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If you just want the script:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by rocky289 on 2012-10-24
Ok, have got it sorted.
Zorin was the last one to be installed & was at the top of the list.
I have made the changes to Grub Customizer & set Ubuntu at the top.
Then under file, installed to MBR.
It is working good now.
 
Thank you to all.
 
Just got to work out how to mark this as solved.

---

### Post by Bucky Ball on 2012-10-24
Good news. Enjoy!

---

