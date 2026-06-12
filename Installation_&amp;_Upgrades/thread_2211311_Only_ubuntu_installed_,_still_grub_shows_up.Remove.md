---
title: "Only ubuntu installed , still grub shows up.Remove grub.Help"
date: 2014-03-15
forum: Installation &amp; Upgrades
---

### Post by manngaurav on 2014-03-15
My Laptop - Acer Aspire 4752 , intel i3-2330M , 500GB HDD , 2GB RAM.
I think it doesn't have UEFI and secure boot etc.. bought it in 2012.


I had win 8.1 , i was very enthusiasticc about ubuntu, download speeds are low here , i had the 13.04 iso so i installed 13.04 and dual booted it. it was like a cake. So now it notified me of upgrading to 13.10 and the upgrade freezed. I cancelled it , downlaoded the 13.10 iso and booted through live usb. It gave me options of upgrading and clean install. 

Unknowingly i clicked on the "ERASE 13.04 AND INSTALL 13.10" , I also checked the encryption boxes and encrypted my drive. Then it was fine , updated BOOTED STRAIGHT IN ubuntu 13.10 , grub didn't show up.(usually the problem is that you boot straight into windows and grub doesn't show up , which is fixed by bootrepair). 

I ran bootrepair here is the my bootinfo BEFORE RUNNING BOOTREPAIR ([http://paste.ubuntu.com/7094954/](http://paste.ubuntu.com/7094954/)).
AND here is the bootinfo AFTER RUNNING BOOTREPAIR. ([http://paste.ubuntu.com/7094973/](http://paste.ubuntu.com/7094973/)).

Now in my  bios there is a strange addition in the boot sequence , which is named ubuntu.  the main HDD 0 is also there. I am very suspicious of that ubuntu label , i don't know where that came form.  

And the grub now shows me three options  1)boot into ubuntu.    2)advanced options in ubuntu.     3)ubuntu/efi/manager(something like this). 

[ATTACH=CONFIG]251173[/ATTACH][ATTACH=CONFIG]251172[/ATTACH]

I am unable to get to my windows :( . 

So after looking at gparted , i realized my windows is gone...now I am pissed off, i thought the upgrade would only mess with the seperate partiton that i had created for 13.04. My data is lost and now my dad is going to kill me , we share the same laptop. :(

I can't do anything now , so rather than banging my head , i have decided to completely switch to ubuntu and see how far can i go.

I want to REMOVE GRUB THAT SHOWS THOSE THREE OPTIONS and boot straight into ubuntu. 

I want to DECRYPT THE DRIVE as it asks for password everytime , which i am sure will annoy other users.(no i am not talking about the login password , my laptop is shared with not so enthusiastic people who wouldn't like to enter the encryption pswd and then the login password of user account.)


Can someone explain to me as to what the drvies are, why is there a key on two of them and why an red exclamation mark on the last one and what does the boot label mean int the last  column of first line.. here in this screencshot.

[ATTACH=CONFIG]251170[/ATTACH][ATTACH=CONFIG]251171[/ATTACH]



And i have the win 8.1 iso , i plan to install it again, can someone help me with the exact process for dual boot as after having delted windows , now i dont want to end up deleting ubuntu .. and the installing it again.

---

### Post by manngaurav on 2014-03-15
i haven't even got any views yet :( . Is there a way to make the thread title interesting....?  I have tried ubuntu for a week or so a year ago , then gave up.(not because i messed up or something, after updating to win8.1 , i lost my ubuntu installation, too lazy to repeat the process again). Nevertheless , just like the quote goes "I have worked too hard to give up now". SO my data is lost,all the files are gone and i am not giving up now. Ubuntu IS going to be my primary OS. Thank you for your time to read my orignal post, it's quite long. :P

---

### Post by ajgreeny on 2014-03-15
Your system **is** installed in UEFI mode and with SecureBoot enabled, about which I can not help as I have never dealt with secure boot on any machine.

I am assuming that Ubuntu still boots and runs as you want it to, and all is well apart from the grub menu appearing even though you only have one OS installed.

I suspect you see the grub menu because you did have windows and will still have an entry in partition sda1 (EFI), for thenow missing windows.  I am not certain if it is possible, or even wise, to open the/boot/efi/EFI folder in nautilus and delete the entry there for windows, which might stop grub appearing at boot time. When I received my new machine early last year with Windows 7 installed in UEFI mode, but not authorized as I did not buy the license, I simply deleted all partitions including the EFI partition and started again by making a new EFI partition and installing in UEFI mode, so I think it is probably safe to delete any windows related folder in /boot/efi/EFI and then think more about installing Win8 again.

It is always easier to install Windows before ubuntu as the Win install will wipe grub as bootloader from the system and replace it with the windows bootloader after which you will have to restore grub, either using BootRepair again or simply using a live ubuntu system.  This used to be very easy pre-UEFI, and may still be so, for all I know, but I have not needed to do this since I have been working with UEFI so am not sure.

You will, however, need to make space for windows to be installed, as it can not properly see, nor work on ext4 partitions, and as you have only the one OS partition which is encrypted that may require extra steps from you that I can not really help with.  I am aware that encryption adds a great deal more security to a system, but from what I have read in many places, it also seems to add so many other potential problems, that I have never felt it worth using.

PS:
**sda1 is your small EFI partition**, mounted at /boot/efi in your ubuntu OS and which you can open and see if it still contains a windows entry.  This is essential for a UEFI installation.
**sda2 is a separate /boot partition**, not normally needed or recommended for ubuntu, but may be for Windows 8 (I don't have windows any more so have no knowledge of that, I'm afraid.
**sda3 is your encrypted OS partition**.

I note you do not have a swap partition which is usually advised, even if you have plenty of ram, though I accept that it is not absolutely necessary, particularly if you have lots of ram in the computer.

---

### Post by manngaurav on 2014-03-16
Phew! after doig loads of searching i found that to remove the encryption from full drvie you have to be super developer who knows just how ubntu works , no I am SURE IT DOESN"T HAVE UEFI and SECURE BOOT. becuase if i had those i wouldn't be able to DUAL BOOT ubuntu with SUCH EASE. i knwo there is a thread or post where it si explained how to dual boot with uefi and that's a lengthy process which i DID NOT have to go through.

And now the swap thing , i have just chosen to erase and do a clean install , so i think ubuntu  SHOULD be taking care of creating root ,swap and home partitions.

SO i put up a torrent whole night and downloade the ubntu ISO YET AGAIN :(. and now i have done a clean install. my above stated problems are removed now.
I still do not see a swap , partiton and i want to know what is the size of my "home" and if i can create a new partition from it...?(From the 465gb space) because gparted doesn't show any options.
NOTE: i have done a complete clean install.
[ATTACH=CONFIG]251200[/ATTACH]

---

### Post by ajgreeny on 2014-03-17
It does not appear to haver secure boot enabled now, or be working in an UEFI install mode as there is no small efi partition on disk as there was previously.
I think it was enabled before as your bootinfo output showed the same paragraph in both versions.

> =================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot enabled.
It would be interesting to see what the script says now, if you run it again on your new installation.

Did you let the system install by default this time to the whole disk?
That is how it looks, though that would normally make sda5 into a swap partition within the extended sda2, the same layout that you have, but your sda5 is unknown for some reason.  Can you run ```
sudo fdisk -l
sudo blkid -c /dev/null
```in terminal, one by one, and report back here the output.  Thast will help figure out how to add swap to your system using the currently unknown sda5

You can make a separate /home partition now, post-installation, if you really want to, but it is not essential now, as it is possible to do a version upgrade and keep your old home files and folders without a separate partition, and even with a separate partition it is always advisable to have a good backup before carrying out the upgrade.

Come back again if you want to consider that.

---

### Post by manngaurav on 2014-03-17
Hey thankyou for your time , i thought i am not going to get a reply anymore. First i booted through the live usb , through gparted wiped out everything. And then did clean install, it's a default install isn't it ? .

No i am not going to run the bootrepair now , because I don't have any problems now , plus this time I didn't choose to encrypt ,so that is also solved , moreover I don't want to risk grub showing up again , so sorry I am not going to run that now.

There is one more interesting thing , I noted that gparted shows the 2gb one as unknown , where as here you can see through the shot of "disks" , there is a swap partition.

[ATTACH=CONFIG]251225[/ATTACH][ATTACH=CONFIG]251224[/ATTACH]

the output of first command , gives me a last line which goes something like swap partition isn't valid , it is bothering me.
[ATTACH=CONFIG]251222[/ATTACH][ATTACH=CONFIG]251223[/ATTACH]

Once again thanks , for your time. :) I love ubuntu yay!

I don't want to make a seperate /home partition . I want to take out 100gb from the 465gb and make it ntfs style and leave it as it is ,  just in case I ever happen to be needing windows again. However gparted doesn't show any options.

---

