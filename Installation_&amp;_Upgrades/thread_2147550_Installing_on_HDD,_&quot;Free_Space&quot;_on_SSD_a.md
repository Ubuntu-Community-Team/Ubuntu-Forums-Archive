---
title: "Installing on HDD, &quot;Free Space&quot; on SSD after accidentally clicking &quot;Revert&quot;"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by TOFFster on 2013-05-22
Hey,

As the title mentions, I was installing Ubuntu onto my HDD in order to dual boot Windows 7 and Ubuntu when I accidentally clicked the Revert button. Don't ask me how I managed it, I have my moments :D

Now the install process says my SSD (Windows 7 install location) is "Free Space" yet I can still boot into it, the files are all here. I'm typing this message from the very system that, according to Ubuntu, doesn't exist.

Now, I'm not sure what this "Revert" button actually does but I assume it reverts the drive selected to its original state. If this is the case it most likely does the wipe after the install process is initiated. Therefore, I exited out of the install process and tried to find a way to remove the settings the install had stored. I have no idea where they are though and burning the original iso to a completely new disc didn't help in the slightest. 

I have however located this file in the directory that was reverted: [http://gyazo.com/c6b86ae3211b1eb1a750cfe5a6b1c68a](http://gyazo.com/c6b86ae3211b1eb1a750cfe5a6b1c68a) EDIT: Scratch that, just noticed the creation date. I assume that isn't the issue.

Would deleting this file and continuing the install process fix the issue?

Thanks,
Lewis Watts

---

### Post by darkod on 2013-05-22
The Free Space can be a result of a corruption or error in the partition table (maybe due to the revert), or a result of fakeraid meta data present on the disk. It can also be a result of switching gpt disk to a msdos disk using windows because it doesn't delete the backup gpt table as it should.

Can you boot into ubuntu live mode and post the output of:
```
sudo parted -l
```

---

### Post by TOFFster on 2013-05-22
Hey,

Thanks for the reply, I'm afraid I'm completely new to Ubuntu and Linux in general. I presume the live mode is the live CD? And I need to input this command into the terminal?

---

### Post by darkod on 2013-05-22
Yes and yes.

Boot with the cd into Try Ubuntu, open terminal and run the command. Copy the output here.

---

### Post by TOFFster on 2013-05-23
Hey,

I've ran that command and was going to screenshot the result but the live environment decided to crash on me and I couldn't be bothered to go through the entire process again. In short, the output said that the partition might be gpt but it might be corrupt or something. Then gave me a y/n prompt asking if I wanted to try and do something I can't remember. If you need more information than that I'll happily try and get the screenshot again but at the moment I have an exam to leave for!

Thanks for the help so far!

---

### Post by darkod on 2013-05-23
Depending what that message about gpt said exactly, it might be the problem where converting from gpt to msdos is not done correctly by windows. Linux can later detect that and gets confused which partition table is used.

If that is the problem, you can remove the backup gpt table with fixparts. Only open the disk with fixparts from ubuntu live mode in terminal, and it will offer to sort out the problem for you.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I don't know if the live session failed because of some issue with your hardware or what. That could be an issue even after you install it, if it has problms with some piece of hardware.

---

### Post by TOFFster on 2013-05-23
Hey,

The only piece of my hardware that is likely to cause an issue is my FX-6300, although I'd be happy to list of my specifications for you if that'd help. I'll have a look into fixparts and see if that solves the problem as soon as I can.

Thanks!

---

### Post by TOFFster on 2013-05-24
Hey,

So once I've loaded this program which specific disk should I be attempting to run this on? The SSD or HDD? I presume the SSD but I'd rather not make assumptions here and risk wiping all of my files :)

Thanks

---

### Post by darkod on 2013-05-24
The program will not wipe anything by default. Also, it doesn't write any new partition table until you tell it to (I think it was the 'w' command).

You need to open the disk where you think you have the gpt problem. I think it was the ssd. But even if you open the hdd with fixparts, no problem. Just exit it and that's it.

So, it would be like:
```
sudo fixparts /dev/sda
sudo fixparts /dev/sdb
```

Note that in live mode fixparts might be gone after you reboot (unless you are using persistancy), so you might need to download and install it again, and run it right away.

---

### Post by TOFFster on 2013-05-25
Hey,

All right thanks, I appreciate the help so far. Will try this as soon as I've finished work on my Windows OS.

Cheers!

---

### Post by TOFFster on 2013-05-26
Hey,

That worked perfectly, thank you very much darkod :D

Although I'm having some minor teething problems with my network connection, it seems to freeze up every now and then and requires a reconnect. Will search for a driver for my adapter that works on Linux in a minute. Any suggestions?

---

