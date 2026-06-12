---
title: "Creating Smart Boot Disk Mgr Floppy Newbie Question"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by chtrace on 2006-12-11
I am having problems getting Ubuntu installed on my desktop. The computer will not recognize the CD. I have tried re-burning the image and changing the boot order with no success.

I am trying now to make a Smart Boot Disk floppy disk to get around this. I went to a link found in this forum and downloaded the following files: rawwritewin, sbootmgr.dks and diskio.dll; I have them in a folder on my desktop(C:\Documents and Settings\home\Desktop\DiskManager Files)

I have opened a DOS window and formatted a floppy in A:

The instructions say to type in  the following commmand at the prompt:
    rawrite -f sbm.bin (rawwritewin.exe sbm.bin)

My DOS promt looks like this: C:\Documents and Settings\home>

I have used the above command as it is written, the first half, the second halve and keep getting the following msg in the dos window:'rawrite is not recognized as an internal or external command...this same msg also applies to:rawwritewin.exe, command,DiskManager

The rawwrite has been unzipped, and set into a folder as mentioned above. I will be the 1st to admit I don't know anything about dos commands, but I seemed to follow the instructions I was given, so please could someone advise me on what I need to do next.

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

The above link is the instructions that I have been using.

I did not install any of the files because it really doesn't 
tell me to install anything. It does say to put the files into the same directory and I assumed that meant the same folder.
Of course assuming always seems to get me in a jam. So any help
or direction would be greatly appreciated.

Thanks to everyone!

---

### Post by goatflyer on 2006-12-11
You need to cd to the directory where rawrite has been unzipped.

Type this command in your DOS window first:
```

cd "C:\Documents and Settings\home\Desktop\DiskManager Files"

```

You need the quotes because your chosen directory name has a space in it.  (Next time choose better! :) )

Prove the rawrite.exe command is really there by typing
```

dir

```

You should see it.  Then type your desired rawrite command with a blank floppy in drive A:

Happy Ubuntuing...

---

### Post by wpshooter on 2006-12-11
If this computer is so old that it will not boot from the CD drive, I am wondering if you should be trying to install Ubuntu on it at all.

How are you going about setting the CD-Rom to be the first boot device ?

Are you actually burning the ISO image to the CD or are you copying it to the CD ?  It needs to be burned NOT copied.

What version of Windows do you have on this computer ?

---

