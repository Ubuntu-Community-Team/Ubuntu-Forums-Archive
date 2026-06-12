---
title: "Hard drive not mounted after upgrades"
date: 2021-07-24
forum: Installation &amp; Upgrades
---

### Post by tribblemaker on 2021-07-24
Hey gang, I got a question regarding Ubuntu updates.  The first time it happened I was thrown for a loop where now I just expect it.  What I've got is a computer that runs Ubuntu and is used as a media server for Plex.  I have Ubuntu, Plex, etc. installed on my primary drive.  No problems there.  However, I have a secondary drive that I use solely for storing media.  Anytime Ubuntu has updates, the secondary drive is no longer mounted when the updates are completed.  After the first time this happened, I figured out that I needed to mount the drive again and then all was right in the world again.  

My question to you guys is, can I do something to keep this from happening?  I took a class on Unix many years ago for which I'm sure I could still dig out my notes on.  No doubt some of the command structure is different on Ubuntu, but I remember one thing we did in class was learn about creating batch files that could run when logging into an account.  Through that I could do things like setup Unix to recognize commands normally used in DOS and such.  I'm sure there are other fun things that can be done.  But in any case, is creating a batch file an option?  Whether it's something that mounts the drive every time I log in or at least checks to see if it's mounted?  Needing some ideas here because I'd love to automate this to where I'm not having to do this anymore.  

Appreciate any input!

---

### Post by grahammechanical on 2021-07-25
Do you have to mount this second drive every time you reboot? Do you reboot every time you update/upgrade? I have a Data partition on a second drive that is automatically mounted because I edited the fstab file. It is found at /etc/fstab.

I got my information from here

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

These are the two lines I added to my /etc/fstab file.

> # to automount Data partition 
UUID=311676c4-ca3e-46d7-8b81-a1a577f601d7 /media/Data ext4 auto,users,rw,relatime 0 2

Something similar might work for you. Perhaps you have already done something like this to your /etc/fstab file. You will need the UUID of the partition on the second that holds the data .

Regards

---

### Post by TheFu on 2021-07-26
/etc/fstab.  This is exactly how Unix does it to, though the device names are different on most Unix systems.  
Unix end-user training doesn't often touch on administrative tasks like mounting storage.

If your 2nd drive uses NTFS, then it is a little harder due to permissions, but you can drastically improve performance with options that no GUI point-n-click provides.

---

### Post by tribblemaker on 2021-07-26
Thanks for the advice! I’ll give that a try when I’m on the computer later. To answer your question, I’d say I’m not certain now if this happens just on upgrades or every restart. I typically only restart after running updates. And no, when I had a class on Unix, batch files were about as in depth as we got with customizing anything. Mainly just involved learning the basic commands and from there some programming in C. But that’s been many years ago now. This here is one of those examples of a prime opportunity to learn some of the more in depth stuff. 

Thanks again guys! I’ll have to reply later and update if this gets fixed.

---

### Post by tribblemaker on 2021-07-29
OK, so I was able to create a modified fstab file.  Took some doing.  Like I said, I'm still learning.  Was struggling with getting it to allow me to replace the file that was there.  Although after what all I did, now I think I could have just edited the file that was there.  Was having permissions issues which I eventually got figured out.  Restarted the computer and everything appears to be working.  The only thing I'm noticing different is it doesn't have the Network Sharing on where before I had that on.  However, I'm thinking I don't really need that on anyway.  I convert my movies on one computer and then transfer to the Ubuntu machine for Plex to use.  But I never could get it figured out how to access my Ubuntu machine from Windows.  On the flip side, I DID figure out how to access a shared folder on my Windows machine from Ubuntu so it all worked out.

Thank you for the advice!  Much appreciated guys!

---

### Post by TheFu on 2021-07-30
To edit system files, use the **sudoedit** command.

Best to always make a backup of the file to be modified first.  **sudo cp /etc/fstab  /etc/fstab-2021-07** It doesn't need to be more than that.

I don't understand the other stuff, due to the lack of details.  Normally, the best way to access storage on Unix systems from any other computer is to use sftp.  WinSCP is the easiest tool for that from MS-Windows.
However, there are also CIFS (samba) and NFS methods too if access using sftp isn't all you seek.  NFS provides native Unix access. CIFS is a lowest-common-denominator option.
The file system used matters for any mounts. NTFS requires some extra hassles and brings some limitations that native Linux file systems like ext4, xfs, ZFS do not have.  Also, NTFS is a little slower - can be 30% slower - than native Linux file systems.

Figuring stuff out is fine, but often doesn't result in the most efficient solution.

For most things that are server related, the Ubuntu Server documentation has to-the-point instructions. Start at help.ubuntu.com - choose the Server release and look for the topic on the left side. There must be 50 topics there. Generally, the Desktop point-n-click solutions are lacking in flexibility, so following the Server instructions that require modifying config files would be preferred.  There are a few exceptions - perhaps 1 in 50 - where the point-n-click answer is the most efficient.

---

### Post by ActionParsnip on 2021-07-30
what is the output of
```

sudo blkid

```
Thanks

---

