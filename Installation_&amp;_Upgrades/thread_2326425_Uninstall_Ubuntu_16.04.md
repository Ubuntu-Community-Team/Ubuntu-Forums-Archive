---
title: "Uninstall Ubuntu 16.04"
date: 2016-05-31
forum: Installation &amp; Upgrades
---

### Post by cobras on 2016-05-31
[COLOR=#000000][COLOR=#000000]I recently acquired a laptop ([/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=arial]Toshiba Satellite C55-A5286, 8GB, Intel(R) Core(TM) i3-3120M CPU 2,5GHz, 700GB HD) running Windows 8, and installed Ubuntu 16.04 along side it.

My question is, how do I uninstall ubuntu?

Thank you for your help.[/FONT][/COLOR][/COLOR]

---

### Post by Bucky Ball on 2016-06-01
You could boot from the USB or disk you installed Ubuntu from, 'Try Ubuntu', once at a desktop launch Gparted, right click and delete your Ubuntu partitions.

This will kill Ubuntu but may leave the Windows unbootable. This can be fixed but knowing nothing about Windows I can't help with that bit, but no doubt someone else can/will. 

Good luck.

---

### Post by cobras on 2016-06-01
That sounds like what I pretty much expected - Ubuntu has killed my Windows OS.  The only way to get it back is to format the HD and reinstall Windows.

---

### Post by mörgæs on 2016-06-01
I don't know what you expected but it was not what Bucky wrote. Ubuntu doesn't kill other operative systems, whatever that means. 

Windows will be untouched but the boot loader might need to be reinstalled. I can't give precise advice on Windows either, leaving others to grab it from here.

---

### Post by Bucky Ball on 2016-06-01
A better option than taking the radical step of wiping the drive and reinstalling everything, which is probably totally unecessary, why not try fixing the Windows bootloader? Can you boot to Ubuntu? If so, open a terminal and put this in:

> sudo update-grub

Hit 'enter'. Reboot. Do you now see Windows on the grub list when you boot the machine? Are you even getting a list of installed OSs? If not, hit the 'shift' key as Ubuntu is booting. 

If you still can't find Windows after doing the above, try [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). Run it but don't repair. Just let it create a bootinfo output file (there is an option on the first screen) and post the link to it here. 

If you haven't wiped the hard drive yet, I'd advise you don't ... yet. This may take five minutes to fix now we know what your actual problem is. It's not that you installed Ubuntu, don't like it, want to remove it. You installed Ubuntu, can't boot into Windows, so you want to uninstall Ubuntu as a remedy to your non-booting Windows. 

If you are going to wipe the hard drive and start from the beginning, you don't need to know how to uninstall Ubuntu. Just wipe the drive. Re-installing Windows will obliterate everything from what I know.

---

### Post by SnazzleLabsYT on 2016-06-01
Here is the best way I have found.
Remove Ubuntu like the way Bucky has written, then get a Windows 8 installer (use your own or use a store bought one), boot it, go to 'Repair your computer' and select 'Command Prompt'. Here, enter the commands;

bootrec.exe /FixBoot

bootrec.exe /FixMbr


[FONT=arial]This should fix your problem. [/FONT]

---

### Post by kansasnoob on 2016-06-01
> **cobras said:**
> That sounds like what I pretty much expected - Ubuntu has killed my Windows OS.  The only way to get it back is to format the HD and reinstall Windows.

Not true!

Are both Ubuntu and Windows bootable? If so we need more info to properly advise you. A good start would be for you to boot into Ubuntu, open the terminal, and post the output of this command:

```
sudo parted -l
```

That will tell us whether this is a standard MSDOS install or a UEFI install as well as showing us what the current partitioning arrangement is.

---

### Post by ajgreeny on 2016-06-01
You have not even told us if you can boot both OSs when side by side on the machine.  Can you??

Let's have a lot more info and we can hopefully help you get back to where you want to be.  The Boot-info-script output from Boot-Repair, see above in BB's post, will be very useful to us; just run the script but don't accept any repair as that may remove Windows bootloader if it is still on the disk.  The script will provide you with a pastebin link with all the info in a long txt file; simply copy that link back here and we can look in detail at where you are at present.

---

### Post by RobGoss on 2016-06-01
You should be able to remove that Ubuntu partition with out effecting your **Windows 8 OS**, I am currently dual booting Ubuntu and Windows 10, from Windows I can use my **disk management** and see my** Ubuntu partition,** if you **right click** on the **Ubuntu partition** and choose Delete volume this should remove your Ubuntu OS and leave you with the **Unallocated** space and from there you should be able to add that space back to your main Windows partition

Also make sure you have a Windows disk in case anything goes wrong 

**Note:** which ever way you choose to do this remember you want to make sure you don't loose that space that was dedicated to Ubuntu you will need to reclaim it back

I would make sure this won't interfere with Windows boot loader before attempting this I've never needed to remove Ubuntu from a dual boot so this is just my assumption but I hope it helps you ether way

---

### Post by yancek on 2016-06-01
If you want to remove Ubuntu or any Linux in a dual boot situation with windows, the first step is as suggested above.  Use the windows installation DVD to repair the boot loader BEFORE you delete the Ubuntu/Linux partition then reboot windows to test.  You can then easily delete the Ubuntu/Linux partition from windows Disk Management.  If you don't have a windows installation DVD, you should be able to download something from microsoft or another windows site to simply repair the bootloader.  If you are using UEFI, it's a totally different story.

---

### Post by cobras on 2016-06-01
OK, thank you for all the feedback.  I'll tell you more.

I am able to launch both OS, but Ubuntu is just not working for me, and I really need a working machine on a daily basis to pay the bills.

This is a used machine bought on ebay with a preinstalled Windows 8 OS.  I do not have the recovery disk.

---

### Post by mörgæs on 2016-06-01
Which kind of problems does Ubuntu make? Chances are they can be solved here.

---

### Post by kansasnoob on 2016-06-01
Just looked at your other posts and I wonder if you're still having network problems?

If so which kernel are you running? You can see by running:

```
uname -r
```

If you've been able to apply the most current updates you should be up to 4.4.0-22 which fixed several networking issues. Of course trying to update without a connection is rather futile unless you have access to a wired connection.

---

### Post by cobras on 2016-06-01
I am having problems with the wifi being so slow that pages time out.  I updated to 4.4.0-22-generic before I posted to the other board.

---

### Post by RobGoss on 2016-06-01
> **cobras said:**
> I am having problems with the wifi being so slow that pages time out.  I updated to 4.4.0-22-generic before I posted to the other board.

What web browser are you using? have you try Google chrome

---

### Post by jeremy31 on 2016-06-01
> **cobras said:**
> OK, thank you for all the feedback.  I'll tell you more.

I am able to launch both OS, but Ubuntu is just not working for me, and I really need a working machine on a daily basis to pay the bills.

This is a used machine bought on ebay with a preinstalled Windows 8 OS.  I do not have the recovery disk.

If you can still boot into Windows 8, you should be able to make a recovery disc and do a full backup- please do both before any attempt at removing Ubuntu.  A search in Windows help should tell you how to make the recovery disc and backup.

You should be able to use virtualisation software in Win 8 to load Ubuntu if you really want to use it and have internet.  You will not be able to control the wifi in the virtual Ubuntu install but it will use a virtual ethernet connection to the Win 8 internet connection

Sorry that we couldn't fix the wifi issues and it can be an issue if you use a lot of different wifi hotspots when you have no control over what type of encryption is used.  Most router manufacturers set the default encryption so that usually you have WPA2 with AES and TKIP.  I have tried using TKIP on my wifi hotspot and the results were very poor

---

### Post by cobras on 2016-06-01
I do not want to lose Ubuntu, so when someone suggests a possible way to save it I'm all ears.

When it was suggested to check which kernel I was running, I went ahead and did so, even though I knew I had run the

[COLOR=#000000][FONT=arial]sudo apt-get update
sudo apt-get dist-upgrade

commands before my original post.  It turned out that I had the latest kernel alright, but it then occurred to me that I had updated with a flaky connection.  Was it possible that the kernel was corrupt?

I went to a local hotspot I knew was just a couple of blocks from the server and updated again.  The connection was much more stable and I could see some serious work getting done.

I think that did it.  Does this make sense?
[/FONT][/COLOR]

---

### Post by jeremy31 on 2016-06-01
It may be an issue with TKIP or a crowded wifi channel.  Watch your other post to see if anything new shows up

---

### Post by cobras on 2016-06-01
I was wrong.  That did not do it.  I left the HOT spot and things are back where they were.  Ubuntu times out while Windows does fine.

One thing I noticed is that at the HOT spot where Ubuntu did as well as Windows, the bitrate was actually lower for Ubunt than the bitrate where I'm at now and pages time out.  The bitrate for Windows is considerably lower but it handles it fairly well, but I can tell it's slower.

If it's a matter of channels, wouldn't it affect both OSs?  I'm posting from Windows, couldn't do it from Ubuntu.

---

### Post by mörgæs on 2016-06-02
The router decides which channel to use. If you have an Android phone the app Wifi Analyser will give a good picture of which channels are congested. 

Before troubleshooting Ubuntu I suggest that you find a place with good Wifi reception or even better, try a wired connection. Does everything work well here?

---

### Post by cobras on 2016-06-17
OK.  I realize now that I failed to give you enough info for anyone to offer an informed response.

Both OS's were bootable after Ubuntu installation, but Ubuntu wasn't acting right.  That's another thread.

Thanks to everyone for your efforts.  I think what made things most difficult for me is that there seems to be no definitive source to go to on this topic.  I followed many threads on this and other forums and finally decided to just try something.

I deleted Ubuntu's partitions and the computer went into a coma.  I then figured out how to repair Windows' bootloader and things seem to return to their original state.

Thank you again.

---

