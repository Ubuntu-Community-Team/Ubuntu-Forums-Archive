---
title: "Dual Booting Issues With Ubuntu, Windows 7, And Windows 10. Yayyy Me!!!! Lol!!!! ;)"
date: 2019-07-30
forum: Installation &amp; Upgrades
---

### Post by koollaydtac on 2019-07-30
So I am going to try and explain this best as possible because I am at a loss. lol I originally installed Ubuntu on a new hard drive I installed. On this drive I have Ubuntu with Windows 10 and it was fine. Had no problems I was aware of originally. I enabled my original main hard drive with Windows 7 on it which I am still currently in the process of trying to fix. The Ubuntu drive is set in bios to boot as the primary drive in the boot order. At some point Grub updated to reflect Windows 7 in the list of bootable OS'es. Far as I knew everything was good and gravy. I been spending so much time on Ubuntu that I haven't bothered with looking at Windows. So I was gone for a bit and came back home finally and for one of the games I play I decided to install it on Windows 10 since I needed to get back to repairing Windows 7 eventually anyway. Just so I'd have something to pass time on. 

Well I went to boot up Windows 10 and it keeps redirecting me to Windows 7. I am like seriously? lol Disabling that drive did not work. I did a Boot Repair as per instructions off the Ubuntu web site and it removed both my MemTest options from the boot list. I tried to fix that and nothing. Reinstall didn't work and I can't just drop the old Grub config back because when I load Grub Customizer it tell me the config changed from what it was when it started up when I go to close out of it without making changes. So obviously I put it back to how it was.

I don't know how to do pastebin so I dropped both configs in a text file and uploaded them to my google drive.

This is before I did the Boot Repair.
[https://drive.google.com/file/d/11xDQX1w5ZXxUAH75TAtxJl1OClwd7ZzQ/view](https://drive.google.com/file/d/11xDQX1w5ZXxUAH75TAtxJl1OClwd7ZzQ/view)

This is the one after I did the Boot Repair.
[https://drive.google.com/file/d/1SVi51D9CkuWuWaoXwPNmGeqVtP_6jXgX/view](https://drive.google.com/file/d/1SVi51D9CkuWuWaoXwPNmGeqVtP_6jXgX/view)

Things I need to know are this. 

1.) How do I add both listings of MemTest back?
2.) How do I fix my OS'es to boot correctly in to their proper listings?
3.) Also I noticed I can not transfer files to my Windows 10 partition from Ubuntu. How do I fix that?

Thanks in advance for any help you all can give. :)

---

### Post by oldfred on 2019-07-30
Better to run Boot-Repair which will automatically upload to a pastebin site.
       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Windows 10 has fast start up which sets hibernation flag. Then you can only mount all NTFS partitions as read only and grub will not boot it.
       
 Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)

---

### Post by koollaydtac on 2019-07-31
I did the boot repair already I just didn't realize I had a pastebin link for it. Sorry about that. 

Here ya go.
[http://paste.ubuntu.com/p/F2BB6SffWV/](http://paste.ubuntu.com/p/F2BB6SffWV/)

Text version.
[http://paste.ubuntu.com/p/F2BB6SffWV/plain/](http://paste.ubuntu.com/p/F2BB6SffWV/plain/)

I followed steps to reinstall in this link as far as trying to add both my Mem Test entries back to the list and it didn't take. I thought reinstalling it would have fixed it, but it didn't.
[https://askubuntu.com/questions/126160/how-can-i-add-the-memtest86-options-back-to-the-grub-menu](https://askubuntu.com/questions/126160/how-can-i-add-the-memtest86-options-back-to-the-grub-menu)

Steps I did were this.
(sudo apt-get install memtest86+
  This will automatically reconfigure grub and add the entry to the boot menu.

  If you get the error memtest86+ is already the newest version then use  sudo apt-get install --reinstall memtest86+)



I am not really sure what other steps I should try on that front. 

As far as Windows 10 goes I looked over the links you provided and thank you for that, but unless I missed something they only tell me how to fix it once I am in Windows 10. I am not booting in to Windows 10 at all mate. In fact when I go to select Windows 10 to boot it up it takes me to Windows 7 which makes absolutely no type of sense at all. lol I am still reading over the last link on boot repairs, but I am so far not seeing anything that explains to me why Windows 10 is booting in to Windows 7 mate. If I work that one out I'll be sure to post it. lol Anyway thanks for the help. I appreciate it mate. :)

---

### Post by oldfred on 2019-07-31
Windows 10 is not the best for dual booting in the old BIOS/MBR configuration.
But you have two drives and then can have Windows boot loader on one drive and Ubuntu's grub on the other drive.
That way when Windows turns fast start up back on & grub will not boot it, you can directly boot from the Windows boot loader in the MBR of the Windows drive.

Normally a new install of Windows overwrites the Boot partition and updates BCD to include both installs.

Boot-Repair says this which is then from Windows 10 fast start up.
       Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.) 
    
You first need to boot into Windows 10 and turn off fast start up. It also may cause issues on Booting Windows 7 as it sets the hibernation flag on all NTFS partitions.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions) 
    
It looks like you did install each Windows separately as grub finds both installs. So two sets of Windows boot files & BCD. Was BCD updates on Windows 10 or are both totally separate. Script will not show internals of BCD and what entries it has.

You also show /grldr. That is from 
       [https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

Best not to use it as it wants you to install grub2 to PBR, partition boot sector of a partition. But grub does not recommend that is it is unreliable. And it uses the very old grub4dos which is based on grub legacy. Having grub in PBR did work with grub legacy, but not recommended with grub2.

Note Windows 7 will reach End of Life next January 2020. 

to fix Windows & turn off fast start up, you will need to install a Windows boot loader to MBR of sdb & boot Windows 10. After fixingWindows,  boot Ubuntu live installer & install grub to sda's MBR. Then set BIOS to boot sda. Then when Windows updates or issues prevent grub from booting Windows, you can switch BIOS to boot sdb & fix Windows. Then boot from sda again. Your reinstall of grub with Boot-Repair looks like a valid install in sda, so you may not need to reinstall.

---

### Post by koollaydtac on 2019-07-31
This is how I initially installed my set up and maybe this will shed some light on it. My original hard drive is 250 gigs and it is the one with the Windows 7 OS installed on it. Currently it doesn't boot up. It keeps restarting which is a separate issue entirely. Long story short that would have been the only drive I used EasyBCD on while booted up in to Hiren's Boot CD that came preinstalled with it and I didn't really even make any changes. I think at best I did a back up and that was it. 

That being said I went and got a second hard drive that was 2 tb. Now what I did with that was I first imaged my original clean copy of Windows 7 and then did the upgrade for it to Windows 10. Keep in mind I have the other drive disabled in bios at this point. So I boot up in to Windows 10 get it all set up and add a virus scanner and what not and then log out of it. 

I boot back up in to Hiren's and break off a chunk of the disk for me to install Ubuntu 18.04 LTS. I let it do it's thing and it set's everything up. At this point I am only having one hard drive enabled at a time. That way while I work on Windows 7 it doesn't interfere with the other drive in any shape or form. 

Well at some point I had decided to make Ubuntu the primary OS and I enabled both drives so I could access files on both placing the 2tb drive first in the boot order. I don't know when, but Windows 7 eventually got added to the Grub list. I thought great saved me the trouble of having to work out how to add it. 

When you say was BCD updates on Windows 10 or are both totally separate. Script will not show internals of BCD and what entries it has. I am not actually sure how to answer that to be entirely honest. Except to say I haven't personally updated or touched anything on either Windows as I have been for the most part on Ubuntu and I sort of been dragging behind on even touching anything Windows related. If I had to guess maybe it's showing /grldr from something I did while trying to repair the Windows 7 hard drive before I set up the other hard drive. I wouldn't have had no reason to work on the Windows 10 since it was a fresh install and booted up fine at the time with no problems.

In all honestly the only reason I even noticed a problem was because I decided to install Fornite on the Windows 10 OS since I knew it currently was working and a clean fresh copy in order to help someone complete some challenges in that game. lol That's how I discovered I couldn't boot in to it any longer or even transfer files over to that partition. Windows 10 is the only OS I have ever seen in my life dual booting has been an issue for me. Any other copy of Windows this would be a non-issue. lol I am not gonna rant, but this is exactly why I'd still remain keeping a copy of Windows 7 even after support for it stops because even with out support it is still the better OS out of all the most recent versions. I am not gonna rant though. I am gonna hush on that note now. lol :D 

Anyway that is how I installed everything best as I could explain it from start to finish mate. Hope this helps. Thanks again for the help. I appreciate it. :)

---

### Post by oldfred on 2019-07-31
I did not know there was a clone so I did not closely look at this:
      ```

/dev/sda1        [COLOR=#ff0000]A68CCE048CCDCECD[/COLOR]                       ntfs       System Reserved
/dev/sda2        [COLOR=#0000ff]9E32CFC332CF9F21    [/COLOR]                   ntfs       
/dev/sdb1        [COLOR=#ff0000]A68CCE048CCDCECD[/COLOR]                       ntfs       System Reserved
/dev/sdb2        [COLOR=#0000ff]9E32CFC332CF9F21   [/COLOR]                    ntfs        


```

You cannot have duplicate UUIDs or if a clone both drives cannot be connected at same time.
Not sure how to change in Windows.
I might just suggest retiring the Windows 7 drive and maybe make it your Ubuntu drive.

---

### Post by koollaydtac on 2019-08-01
I didn't catch that either mate. I thought it was different after I installed Windows 10. I probably wouldn't have thought of that anyway given until Windows 10 I never had a conflict setting restored fresh OS'es on newer drives. That I can recall anyway. Then again could have been how I did it back then that was different so it was never a conflict. I mostly swapped the boot order out in bios for the drive I wanted as a primary. This is the first time in ages I have tried using a boot loader to organize my OS'es. 

That being said I did try disabling the Windows 7 drive in bios in order to remove that drive entirely from the equation for now to see if Windows 10 would boot up, but I got an error message telling me your pc needs to be repaired and the required device isn't connected or can't be accessed. It's acting like it can't find the winload.exe, but I checked and it's there. Given I can't transfer files to that partition currently I am willing to bet it's more likely it can't be accessed. I think once I get that part resolved that will be half my battle and everything else should hopefully fall in to place. 

That was a good catch on the UUID's though btw. I had to laugh because I had a duh moment as many times as I pulled it up in Grub customizer and it never once clicked they were the same. lol Thanks again for the help mate. :)

---

### Post by oldfred on 2019-08-01
Grub only boots working Windows. That also means it cannot be hibernated and fast start up sets hibernation flag. So you can only directly boot Windows from MBR. Or need to temporarily restore a Windows or Windows type BIOS boot loader to MBR. After fixing Windows or turning off fast start up, then restore grub to MBR.

With newer UEFI you can always directly boot Windows from UEFI. And since Windows likes to turn fast start up back on, or may need chkdsk after an issue, you need to be able to directly boot Windows. 
Since you have two drives, it would be better to use both MBR, one with grub & one with Windows boot loader. Those with one drive find Windows 10 in BIOS/MBR mode a bit of a hassle on boot loaders & making repairs.

I might just install Ubuntu one the current Windows 7 drive. Then you can always boot Ubuntu from one drive and Windows from the other drive.

---

### Post by koollaydtac on 2019-08-12
Ok This is where I am at right now. I tried bootrec /fixmbr and it removed grub on me. So I went on and followed threw with step found in this guide.
[https://easylinuxtipsproject.blogspot.com/p/windows-7-boot.html](https://easylinuxtipsproject.blogspot.com/p/windows-7-boot.html)

I'll also drop screen shots of what happened when I did it. I was in Hirens Boot Cd at the time I did this.

[https://cdn.discordapp.com/attachments/558632421608783891/609849828310122508/unknown.png](https://cdn.discordapp.com/attachments/558632421608783891/609849828310122508/unknown.png)

[https://cdn.discordapp.com/attachments/558632421608783891/609849929652764673/unknown.png](https://cdn.discordapp.com/attachments/558632421608783891/609849929652764673/unknown.png)

When I did the nt60 all /force commend I am not sure if it messed with my usb drive or not. It seems ok so far. Long story short I manage to get Windows 10 back up and booting after those steps. 

So my question now is this. Is this the only method of restoring the Grub menu back? Also how would I readd Memtest and Memtest x86 back again?
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Reason I am asking is because I thought I read some where there was a way to restore it in the mbr without actually needing to reinstall the whole thing all over again. I just can't find where I read that at again. I am hoping re-adding grub won't mess it up all over again. I'd prefer to hang on to Windows 7 for as long as humanly possible. 

One thing I have noticed with Windows 10 is once I turned off fast start it seems to have removed it from the menu all together. So I have no way of knowing if it turns back on or off. Also i saw no way to turn off hibernation so I did it in command prompt with the command powercfg.exe /h off so I am assuming that worked for it. 

The Windows 7 drive I currently am keeping disabled until I can repair it and change the uuid on it. At this stage I don't really want to risk running both drives at the same time until I can resolve the conflict between the two. I get what your saying though about making it the Ubuntu drive and it probably would be easier, but in all honesty I've already set up the OS and if I were going to drop Windows 7 for Ubuntu it'd probably be a downgraded secondary copy of Ubuntu 14.01 LTS I think it is called because that one would work with the proprietary drivers for my video card and would allow for me to run some of my higher end games I would think where as currently I can not on Ubuntu 18.04 LTS. Which is fine because there are some things about 18.04 that I do like which is why I'd want to stick with it. 

Anyway that's sort of where I am at with everything right now. Thanks again for the help mate. :)

---

### Post by oldfred on 2019-08-12
Most find Boot-Repair the easiest way to restore grub. If can just install grub to MBR, or if bigger issues, do a full uninstall/reinstall of all of grub2 resetting all parameters.

You can use Boot-repair's advanced mode and install grub to MBR of old drive and keep Windows boot loader on main drive. Otherwise you have to go thru the restore Windows boot loader, repair Windows & then restore grub every time Windows has issues.

Before Boot-Repair you could just restore grub to MBR with a few commands. More commands if full replacement of grub and if major issues a full chroot into broken system from live installer to do major repairs. Boot-Repair can in advanced mode do most of those repairs.
Or full reinstall & restore all data from backups.

       #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

