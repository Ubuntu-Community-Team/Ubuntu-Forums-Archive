---
title: "Installing Ubuntu ISO by commands"
date: 2020-03-10
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2020-03-10
What is the best method for installing and running an ISO using commands?
I have no desktop or external drive facility. Do the partitions need adjusting?
Is it better to use Grub2  or the tty1 screen?

---

### Post by sudodus on 2020-03-10
What have you got?

What computer is it (brand name and model) and what operating system is there?

If you are running Ubuntu Server, it should be possible to modify the grub system to add a menuentry that lets you boot from an iso file stored in the internal drive. See this link: [help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

---

### Post by angel mike on 2020-03-10
Thanks sudodus for that quick response.
Dell Laptop XPS13 7390
OS Ubuntu 18.04
Dell provide no support for Linux although they sell them - only Windows. They removed the option to boot from an external drive which I had on my Dell XPS11. In removing a dbus.file and its deficiencies I lost the GUI - tried reinstalling it but gives errors and cannot fetch archive files - so best option seems to be reinstall the OS.
I have seen a lot of references to a Server - can the same method be used for a laptop?

---

### Post by CelticWarrior on 2020-03-10
> **angel mike said:**
> Dell Laptop XPS13 7390
OS Ubuntu 18.04
Dell provide no support for Linux although they sell them - only Windows. 

Vendors support the preinstalled OS only in consumer products. Dell doesn't support Windows in the Developer Editions (Ubuntu) either.

> They removed the option to boot from an external drive which I had on my  Dell XPS11.
No, they didn't. What made you think that?

>  In removing a dbus.file and its deficiencies I lost the GUI  - tried reinstalling it but gives errors and cannot fetch archive files  - so best option seems to be reinstall the OS.
Are you sure you were connected to the internet?

> I have seen a lot of references to a Server - can the same method be used for a laptop?
The reference to "server" above is regarding the Ubuntu Server edition.


This looks like a X-Y problem: You can't boot installation media and instead of asking for help for that issue you're asking about what you think is a solution, booting an installation ISO in an internal drive or something, or "Installing Ubuntu ISO by commands"...

---

### Post by sudodus on 2020-03-10
I agree with @CelticWarrior, that you should be able to boot your Dell laptop from a USB drive, with some help from us and the following links:

[help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Why Doesn't my Bootable USB Boot](https://askubuntu.com/questions/1186435/why-doesnt-my-bootable-usb-boot)

---

### Post by mörgæs on 2020-03-10
> **angel mike said:**
> Dell Laptop XPS13 7390

With hardware as new as this 19.10 is probably a better option.

---

### Post by angel mike on 2020-03-10
Thanks for all your responses - I am grateful.
First the Laptop came with Ubuntu preinstalled not Windows.
Dell have confirmed that the Boot Option for external drives was removed because customers never used it.
They admitted that they only have support for Windows and sent me off to get in touch with Canonical who promptly said they only support their own paying Enterprise customers.
Dell are now searching for someone else to provide support - unbelievable !! The machine is only 3 moths old and still under warranty - yet they say its outside the return period. I say the return period is invalidated by the fact they only support Windows machines. 
So booting using the BIOS with an external drive is definitely out. 
So unless there is a way of using the Grub2 to boot or retrieving the GUI ( which I have tried unsuccessfully) the only other option is downloading the ISO and running from the ttty1 or Grub2.
I am not too familiar with partitioning and constructing a menuentries - but willing to persevere - I have lost faith in Dell..

---

### Post by sudodus on 2020-03-11
1. The advice from the Dell helpdesk could be wrong - there might be a way to boot from an external drive (for example USB pendrive or memory card or DVD drive via USB).

2. Another option is to unplug the internal drive from your problematic Dell laptop, connect it to another computer and install Ubuntu into it while in that other computer. As long as you avoid proprietary drivers, the installed system will be portable, and it is likely to work, when moved back to your Dell laptop.

3. You could even tell the Dell support people to send a fresh internal drive with a working Ubuntu system already installed.

4. Several experienced Ubuntu users in the UK are active at our Ubuntu Forums. If you are lucky, you live close to someone, who might be able to help you, if you can can bring your laptop to her/him.

---

### Post by angel mike on 2020-03-11
Thanks sudodus for those interesting comments.
Plugging in a USB or CD disc does not work.
Not sure how I find an experienced user near Worcester UK = any offers out there?
 How do you unplug the internal drive ?

Is it worth trying another tackby converting to a Sever and then re-installing the GUI using something like
sudo apt-get install tasksel
sudo tasksel remove ubuntu-desktop
sudo tasksel install server

Have tried 
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop

This gives a lot of errors about missing items.

---

### Post by P-I H on 2020-03-11
Have you tried to enter BIOS and change boot device to USB?

Information from Dell support to enter BIOS:
1 Entering BIOS setup program
2 Turn on (or restart) your computer.
3 During POST, when the DELL logo is displayed, watch for the F2 prompt to appear, and then press F2 immediately.
4 NOTE: : The F2 prompt indicates that the keyboard is initialized. This prompt can appear very quickly, so you must watch for it, and then press F2. If you press F2 before the F2 prompt, this keystroke is lost. If you wait too long and the operating system logo appears, continue to wait until you see the desktop. Then, turn off your computer and try again

---

### Post by yancek on 2020-03-11
>  In removing a dbus.file and its deficiencies I lost the GUI - tried  reinstalling it but gives errors and cannot fetch archive files

You bricked the GUI, but can still boot your Ubuntu but without a GUI, is that correct?  Additionally, for some other reason(s) you are unable to boot from a DVD/USB on this new compter, correct?  I've not used Dells so am very surprised at the comments in post #7 about support or lack of it.  Obviously, Canonical doesn't provide support unless it is paid for but I would certainly expect them to support a system which they sell with Ubuntu installed.  Not sure about the disabling booting from the external drive and similar since Dell is basically an 'assembler' of hardware they purchase from other, AFAIK.  .

After reading through your posts several times, it seems that due to the inability to use the GUI, you want to download or use a current Ubuntu iso and install Ubuntu again to another partition on the internal or external drive, is that correct?  If it is, that is a very simple thing to do as Grub2 has supported booting from an iso for years.  All you need do is put a proper entry in the /boot/grub/grub.cfg file for a one time boot, create an ext4 formatted partition on the same or another hard drive on which to install it.  If this is what you want to accomplish there are numerous explanations of how to boot an iso directly with Grub2 and many of them are specifically for Ubuntu.  If you have trouble determining how to create a proper boot entry, post back.  The site below is the Ubuntu documentation on the subject and I would suggest scrolling down to the section beginning with "Manually Editing the Grub Files" which has example entries.

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

---

### Post by angel mike on 2020-03-11
Thanks but P-I H Yes did that as first step - no option for external  drive

---

### Post by sudodus on 2020-03-11
- If ***you*** live near Worcester UK, can you help angel mike?

- Q: How do you unplug the internal drive? A: This should be explained in your user's manual (in paper or as pdf file or as web page) for the computer. Can you find it yourself or do you need help?

---

### Post by sudodus on 2020-03-11
> **angel mike said:**
> Thanks but P-I H Yes did that as first step - no option for external  drive

Sometimes the USB pendrive can be regarded as one of the hard disk drives. See [this link](https://help.ubuntu.com/community/Installation/FromUSBStick/bootUSB#Select_.27hard_disk.2FUSB-HDD0.27)

---

### Post by oldfred on 2020-03-11
These are all similar models of Dell.
And all these users seem to be able to make it work.
I have seen several users with Dell pre-installed Ubuntu upgrade to a newer Ubuntu version, not sure if any were as new as yours. Some with newest systems need newest Ubuntu for latest drivers or may need drivers from Dell's sputnik.

Dell 7791 UEFI update & some settings
[https://ubuntuforums.org/showthread.php?t=2431450&page=3](https://ubuntuforums.org/showthread.php?t=2431450&page=3)
Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options)
[https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1](https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1)
[https://ubuntuforums.org/showthread.php?t=2431791](https://ubuntuforums.org/showthread.php?t=2431791)
Dell XPS 15 Series 7590 (2019)
[https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590](https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590)
[https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019](https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019)

New Dell 2020 & Sputnik history
[https://bartongeorge.io/2020/01/01/introducing-the-2020-xps-13-developer-edition-this-one-goes-to-32/](https://bartongeorge.io/2020/01/01/introducing-the-2020-xps-13-developer-edition-this-one-goes-to-32/)
[https://www.dell.com/support/article/uk/en/ukdhs1/sln310507/ubuntu-based-developer-and-engineering-systems-project-sputnik?lang=en](https://www.dell.com/support/article/uk/en/ukdhs1/sln310507/ubuntu-based-developer-and-engineering-systems-project-sputnik?lang=en)
Dell XPS 13 9380 Developer Edition Now Available, Shipping With Ubuntu 18.04 LTS
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-13-9380-Developer](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-13-9380-Developer)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

---

### Post by angel mike on 2020-03-11
Thanks yancek - I am extremely encouraged by your post. You are correct in all your assumptions - yes I feel the best option is to install a new version of Ubuntu using Grub2 which I have. I am fairly well versed in booting from usb's - my last was a Dell XPS11 which came with Windows -I changed that to Ubuntu then back again to give it to someone else. I assumed the same would apply to the XPS13.
The BIOS is UEFI and definitely does not have the option for external drives,  Using the Chainloader suggested by sudodus link to boot from Grub2 does not work with UEFI.
At the moment I am in a difficult position since if I modify the laptop in anyway without Dell approval it could invalidate the warranty. So I am waiting on them to find support. Dell technical went away to find some more support and gave me two links - both to Canoncal ( Sales/Enterprise support) who have already refused to help!
I am aware and have read your link several times before - I am just a bit unsure of setting it all up but it seems the best option. So when Dell give me the all clear I will post my list commands and hopefully someone will comment on them before I apply them.
Thanks once again for all the contributions from the forum.

---

### Post by yancek on 2020-03-11
I don't have a Dell computer to check and am not familiar with their BIOS firmware but on my HP, there is no specific option to "boot from an external" drive.  When I access the boot options, if I have an external drive attached it will show in the boot options.  I have a Seagate external drive and it shows there.  If I have a bootable flash drive it will also show up.  If it is capable of UEFI and Legacy, two options will show by name of manufacturer (Sandisk, Toshiba, Lexar or whatever) and one of the options will contain "UEFI".

You don't need to have that option all you need is a correct entry in the grub.cfg file on the installed Ubuntu pointing to the correct drive and partition which you can check with sudo fdisk -l while booted to your installed Ubuntu.
The entry below is a template for the menuentry you would need which works for most Ubuntu derivatives I have used.  You would need to change the loopback loop line as it shows (hd0,gpt3) which is equivalent to sda3.  Get the correct drive and partition here and the entry is case sensitive so enter it exactly.  Also on the linux line the filename needs to be exact.  The entry indicates that it is in the / or the partition so if you have it elsewhere such as your Downloads folder, you would need to change the path on the loopback loop line, i.e.: /home/username/Downloads/ubuntu-18.04.4-desktop-amd64.iso.  If you get an error, make sure to make a not of it to post back.  

> menuentry "Ubuntu" {
    loopback loop (hd0,gpt3)/ubuntu-18.04.4-desktop-amd64.iso
    linux (loop)/casper/vmlinuz boot=casper persistent  iso-scan/filename=/ubuntu-18.04.4-desktop-amd64.iso
     initrd (loop)/casper/initrd.lz
}

---

### Post by P-I H on 2020-03-12
As yancek writes, you have to have the installation media attached to have the possibility to select the boot device in BIOS. This is the case on my motherboards from Asus, and MSI. On my MSI motherboard I also have to select a specific USB port.

---

### Post by yancek on 2020-03-12
>  As yancek writes, you have to have the installation media attached to have the possibility to select the boot device in BIOS. 

I guess we are reading the question/problem the OP is having differently.  The way I read it, there is no need for an attached installation media as the OP will have the Ubuntu iso on the hard drive from which he is booting his installed Ubuntu.  That's my reading.  So then he would simply need to put a proper entry in the /boot/grub/grub.cfg file of the installed Ubuntu OS, reboot and select that menuentry to begin using the Ubuntu 'live installer' in the same manner as if booted from a DVD or USB.  This option has been available with Ubuntu for a number of years.  Maybe I'm not reading the problem the OP has correctly??

---

### Post by angel mike on 2020-03-12
I have inserted the usb drive and a dvd player(official disc version) before booting  and the entered the BIOS  to see if they had been recognized  then let exit and continued  the boot . None were recognized - they have been used on my XPS11 so I know they work. There is an option to add a boot option but it only lets you search for a file. So I will look at setting up the ISO install. 
What is the best command to check whether the vmlinuz  and initrd files are installed and if not do I need them?
 grub>ls      gives partitions (hdo)  (hdo,gpt1) (hdo,gpt2) (hdo,gpt3)
grub>ls /sys/firmware/efi      gives 'not found' message so system is using the BIOS and there is no vmlinuz and initrd files as this folder is missing

I just found an iso in the Downloads folder using the tty1 screen

$ ls Downloads      gives a list of files and one of which is 'factory_image.iso'

Sorry I am being lazy and not using the  '/code' format on the commands

---

### Post by P-I H on 2020-03-12
I might be wrong, but as far as I know the boot media/device must be recognized by BIOS and you select the boot media/device in bios. Others have had problem with this Dell computer. this is a link to a discussion and a solution.
[https://www.dell.com/community/XPS/XPS-13-Developers-edition-new-one-2019-won-t-boot-from-USB/td-p/7410750](https://www.dell.com/community/XPS/XPS-13-Developers-edition-new-one-2019-won-t-boot-from-USB/td-p/7410750)

"Re: XPS 13 Developers edition (new one 2019) won't boot from USB
okay, solved. The solution is simple - only Ubuntu 18.04 has GPT extended boot loader definition in the iso. PopOS / Fedora does not have. XPS 13 7390 confirmed to install Ubuntu."

In case it is possible to boot the PC the advice from [COLOR=#000000]*yancek *[/COLOR] ought to work. I have however never done this before.


[COLOR=#000000][I]
[/I][/COLOR]

---

### Post by yancek on 2020-03-12
> What is the best command to check whether the vmlinuz  and initrd files are installed and if not do I need them?
 

If you are in fact, able to boot Ubuntu without a  GUI, you can use a text editor (as root, using sudo) to edit the /boot/grub/grub.cfg file on the installed Ubuntu.  The vmlinuz and initrd files are contained within the iso so I don't know where you are looking.  Obviously, you won't see them in the iso unless you loop mount or extract the folders/files on the iso.

> grub>ls      gives partitions (hdo)  (hdo,gpt1) (hdo,gpt2) (hdo,gpt3) 

That tells how many partitions you have and that they are GPT but it doesn't tell where the installed Ubuntu is.  Again, you need to boot the installed Ubuntu and determine on which partition it is.  You can do this from a terminal running the command:  df -h   On my laptop, Ubuntu is on sda6 and this is the output I get, the / shows where the root of the filesystem exists.

> ~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        50G   15G   33G  31% / 

I have no idea what factory_image.iso is.

I'm not sure where you are looking for the vmlinuz/initrd file or why since those files are contained within the iso you want to boot.  The output in your last post indicates that you have a GPT drive and that it is apparently not EFI per the output you posted so you should have an unformatted 1-2MB partition shown as bios_grub.

---

### Post by angel mike on 2020-03-14
yancek - should the loopback loop include the (hd0,gpt3) followed by the /home/michaelb/Downloads/......
If so how do I confirm that the Downloads file is in (hd0,gpt3) partition?

---

### Post by yancek on 2020-03-14
>  should the loopback loop include the (hd0,gpt3) followed by the /home/michaelb/Downloads/....

The menuentry posted below is an example.  You need to run the df -h OR sudo df -h command to find out where (which partition) your Ubuntu is installed.  The example below shows an Ubuntu iso file on the first hard drive, 3rd partition so you need to change that to whatever is correct for you system.  You may not need the (hd0,gpt3) after loopback but I would leave it and you could also include the set root line shown below with the correct drive/partition.  If your Ubuntu iso is in the user Downloads file, then you should include that full path:  /home/micahelb/Downloads and it should boot.  Everything in the menuentry outside the menuentry line itself in quotes is case sensitive.  Make sure you have a number zero (0) and don't accidentally hit the lower case Letter O.

One possible problem would be  if you have a separate partition for /home, that would mean a different partition.  You can verify this by looking at the /etc/fstab file to see if there is a separate entry there for /home which is not likely to be the case.

> menuentry "Ubuntu" {
set root='hd0,gpt3'
    loopback loop (hd0,gpt3)/ubuntu-18.04.4-desktop-amd64.iso
    linux (loop)/casper/vmlinuz boot=casper persistent  iso-scan/filename=/ubuntu-18.04.4-desktop-amd64.iso
     initrd (loop)/casper/initrd.lz
} 			 		 

---

### Post by oldfred on 2020-03-14
Someone with a Dell and Ubuntu pre-installed had posted a Boot-Repair report.
It showed an extra grub entry & partition with an Ubuntu recovery partition. Did not get into details on that.

If you press escape right after Dell logo, do you get grub menu? And option to boot recovery?

---

### Post by angel mike on 2020-03-15
Have the grub screen but only gives grub>
Have typed the menu entry into the grub screen pressed enter with no errors coming up then typed boot and it gave the error 'you need to  load the kernel  first.
So presumably the files linuz and initrd are missing

Using the tty1 screen to enter the menuentry I get the error 'bash: syntax error near unexpected token '('

Also used the grub> screen and then grub> boot but but got ' error : you need to load the kernel first '

Then I noticed on reading the guide section Booting without a GRUB Menuentry that you should leave the title line off. 
So will try again but it says type in each line - does this mean I type the layout as given in the examples ? I guess it does.
Have not read some of the posts yet but have mounted the factory_image.iso and it contains 15 files in blue colour , 2 white and 1 green. No vmlinuz, or initrd files or are they in one of the files listed?

---

### Post by yancek on 2020-03-15
> Using the tty1 screen to enter the menuentry I get the error 'bash: syntax error near unexpected token '('
 

Whatever line you entered had a " ( " when there should not be one but you haven't posted the line so...?

> So will try again but it says type in each line - does this mean I type the layout as given in the examples ?  

What examples are you referring to?  When you are trying to boot from a grub prompt, you enter each line and then hit the Enter key to get the next line.
Are you trying to boot the factory_image.iso?
Are you trying to boot the installed Ubuntu?  Still isn't clear to me if you can do that.

---

### Post by angel mike on 2020-03-15
Typing df -h in the tty1 screen gives a list of 7 Filesystems, Apologize for not posting but have yet to master that ( I have seen the key sequence for copy and paste in the terminal and also putting the output in a file) 
3 have zero. 
The 2 which I think of interest are 
/dev/nume0n1p3   Size463G    Used43G   Mounted on /
/dev/nume0n1pt1          776M           36M                      /boot/efi

So what  do I use instead of (hd0, gpt3). Looks like Ubuntu is the / with (hd0,3)

I have been typing the whole of the menuentry without pressing the ENTER key both in the grub and tty1 screens. 

Used loopback loop (hd0,gpt3)/home/michaelb/Downloads/ubuntu-18.04-desktop-amd64.iso

I will look at the link posted by P-I H

---

### Post by yancek on 2020-03-15
> Typing df -h in the tty1 screen gives a list of 7 Filesystems 

Do you mean you have 7 different partitions with filesystems?  What does "3 have zero mean?  Are 3 partitions empty, no data?

> /dev/nume0n1p3   Size463G    Used43G   Mounted on /
/dev/nume0n1pt1          776M           36M                      /boot/efi 
.
The first line above is where the Ubuntu system is installed because it shows:  mounted on / (the / is a symbol for the root of the filesystem)
The second line shows that you have a EFI partition.

> Used loopback loop (hd0,gpt3)/home/michaelb/Downloads/ubuntu-18.04-desktop-amd64.iso 

I still don't know if you can boot the installed Ubuntu, can you.  You've indicated you have no GUI but can you boot the system to access a konsole/terminal?  If you can do that, you can just put the menuentry in the /boot/grub/grub.cfg file.  You need root access so you would need to use sudo nano /boot/grub/grub.cfg to open it (nano is a text editor so if you use some other text editor, substitute the name on that line).   

If you are unable to boot the installed Ubuntu but when you boot, you get a grub prompt (grub>) the link below gives an explanation with examples of doing this.

[https://www.linux.com/tutorials/how-rescue-non-booting-grub-2-linux/](https://www.linux.com/tutorials/how-rescue-non-booting-grub-2-linux/)

The link below has an explanation also about half way down the page and remember these are examples and you are not using (hd0,1) but (hd0,3).  I'm not sure about the device as I don't use SSD's?

[https://askubuntu.com/questions/929833/how-do-i-boot-my-pc-from-grub](https://askubuntu.com/questions/929833/how-do-i-boot-my-pc-from-grub)

---

### Post by angel mike on 2020-03-15
I have solved it!
i forgot that I put the Dell Recovery File on a USB.
So using the F12 key the USB was recognized - so the laptop is loading up the factory installed software. Fortunately I had backed up my files.
I think the USB I was trying to use to loadup a new version of Ubuntu was not UEFI enabled. I did not realize the difference between Legacy and UEFI.
Thanks to everyone who made a posting - I have learnt a lot about using the/editing from the Grub and Terminal.
Pity Dell could not ask me if I made a recovery file USB,
Sorry for all the time spent.

---

### Post by yancek on 2020-03-15
>  I did not realize the difference between Legacy and UEFI. 

You can find all the info on that subject regarding Ubuntu at the official documentation site below.  Might be worthwhile to bootkmark it.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ping-wu on 2020-03-15
> **yancek said:**
> 
[COLOR=#000000]*menuentry "Ubuntu" {*[/COLOR]
[COLOR=#000000]*set root='hd0,gpt3'*[/COLOR]
[COLOR=#000000]*loopback loop (hd0,gpt3)/ubuntu-18.04.4-desktop-amd64.iso*[/COLOR]
[COLOR=#000000]*linux (loop)/casper/vmlinuz boot=casper persistent iso-scan/filename=/ubuntu-18.04.4-desktop-amd64.iso*[/COLOR]
[COLOR=#000000]*initrd (loop)/casper/initrd.lz*[/COLOR]
[COLOR=#000000]*}*[/COLOR]


Thanks for the example.  But may I ask where will this persistent option store the persistency?  Thanks.

---

### Post by sudodus on 2020-03-16
If there is a file with the name 'casper-rw' or in some (but not all) cases a partition with the label 'casper-rw', and it can be found during the boot process, it will be used for persistency.

Edit: In the next LTS version, Focal Fossa to be released as Ubuntu 20.04 LTS, the corresponding name or label will be 'writable', and a partition will work in more cases than in 18.04 LTS.

---

### Post by ping-wu on 2020-03-16
> **sudodus said:**
> If there is a file with the name 'casper-rw' or in some (but not all) cases a partition with the label 'casper-rw', and it can be found during the boot process, it will be used for persistency.    

Thanks!

> **sudodus said:**
> Edit: In the next LTS version, Focal Fossa to be released as Ubuntu 20.04 LTS, the corresponding name or label will be 'writable', and a partition will work in more cases than in 18.04 LTS.

Has this already happened?  My LiveUSB with the casper-rw partition no longer works (no longer boots).  Please see:

[https://ubuntuforums.org/showthread.php?t=2438655](https://ubuntuforums.org/showthread.php?t=2438655)

---

### Post by ping-wu on 2020-03-16
> **ping-wu said:**
> Has this already happened?  My LiveUSB with the casper-rw partition no longer works (no longer boots).  Please see:

[https://ubuntuforums.org/showthread.php?t=2438655](https://ubuntuforums.org/showthread.php?t=2438655)

I am answering my own question.  The answer is YES, the persistent partition must now be labelled **"writable"** (and not "casper-rw") for the persistency to go into effect.

I have just made a persistent Kubuntu 20.04 LiveUSB, and it works as expected.  I am sure the same steps will work for Ubuntu 20.04.

---

### Post by sudodus on 2020-03-16
Yes, you are right: The version of Focal Fossa, that you get via the current daily iso files want the name/label 'writable'. This affects standard Ubuntu and all community flavours, because they use the same version of the casper package.

You find more details at [this bug report](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1863672).

---

### Post by yancek on 2020-03-16
> But may I ask where will this persistent option store the persistency?  

As far as I can see, the OP had no persistent file/partition so I should have left that part out of the example I posted but using persistence is explained in the posts above.

---

### Post by ping-wu on 2020-03-16
> **sudodus said:**
> Yes, you are right: The version of Focal Fossa, that you get via the current daily iso files want the name/label 'writable'. This affects standard Ubuntu and all community flavours, because they use the same version of the casper package.

You find more details at [this bug report]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1863672").

Thanks a whole lot!!!

---

### Post by ping-wu on 2020-03-17
> **yancek said:**
> [COLOR=#000000]*menuentry "Ubuntu" {*[/COLOR]
[COLOR=#000000]*set root='hd0,gpt3'*[/COLOR]
[COLOR=#000000]*loopback loop (hd0,gpt3)/ubuntu-18.04.4-desktop-amd64.iso*[/COLOR]
[COLOR=#000000]*linux (loop)/casper/vmlinuz boot=casper persistent iso-scan/filename=/ubuntu-18.04.4-desktop-amd64.iso*[/COLOR]
[COLOR=#000000]*initrd (loop)/casper/initrd.lz*[/COLOR]
[COLOR=#000000]*}*[/COLOR]

BTW, have you ever recently encountered this bug (when booting directly from iso)?

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311)

---

### Post by sudodus on 2020-03-17
@ping-wu,

Yes, *This bug affects me and 13 other people* (that grub 2.04 cannot boot from a loop mounted iso file).

---

### Post by yancek on 2020-03-17
> BTW, have you ever recently encountered this bug (when booting directly from iso)?
 

No because I am still using Grub 2.02 and generally put iso files on a flash drive.  Apparently, there is a problem with Grub 2.04.

---

