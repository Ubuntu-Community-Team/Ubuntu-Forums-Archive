---
title: "[SOLVED] Is there an optimal partitioning scheme for encrypted &quot;home&quot; folders?"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by Fernando Negro on 2013-03-21
I've partitioned (by hand, and using a specialized tool/distro) a hard drive, using a "GUID Partition Table" (GPT) - with an exact (to the byte, non-2MB(?) interval) partition alignment - where I've created a separate /home partition, in which the several "home" folders are stored encrypted and are then decrypted when a user logs in.

(I'm using Xubuntu 12.04, on that machine.)

However (lately, at least) the login process (with the decrypting process also presumably included) takes a very long time to finalize, and I have to wait about a minute, or so, before effectively entering an account on that computer.

And I suspect this is because of something in the decryption process that is taking a very long time to do. Which I find strange, since this is a recent and fast computer, which (at first, I think, wouldn't be as, and) shouldn't be this slow in this process.


The partitioning scheme I'm using is:

(1) a small 2 MB (required) partition, to adapt the hard drive to the non-EFI (BIOS) boot;
(2) an ext4 partition, for the OS itself ("root");
(3) an ext4 partition, for /home;
(4) and an encrypted swap partition.


When I let Ubuntu make the partitioning itself, in an installation process, and I choose for it to encrypt the "home" folders, I can see that it creates some MBR (non-GPT) extended and logical partitions(?), of variable size, instead of the fixed size that I'm using.

So, I suspect this might be the reason for the computer taking so much time decrypting the home folders.

*(And I doubt it has anything to do with finding space to decrypt to, on that hard drive, since it is a very big one, with a huge amount of, and more than enough, free space...)*


Can anyone here tell me if my suspicion is right?

*(Or does the decryption process usually takes a long time, because of the amount of files involved?) (Like I said, I don't remember it taking this much time in the first logins...)*

And, if my suspicion is right, what is, then, an optimal partitioning scheme to use with encrypted "home" folders?


Note: This does not happen *every* time, when I login... However, it does happen *most* of the times, now (from what I can notice and remember)...

---

### Post by oldfred on 2013-03-22
You only have to have gpt on drives over 2TB. But I think Ubuntu installs with gpt if drive is blank somewhere over 1.5TB. 
Arch also recommends gpt for SSDs.
Windows only boots from gpt drives with UEFI and UEFI requires gpt. All new Windows 8 systems are gpt.

I now only use gpt (with BIOS) for new drives but do not use encryption. What I have seen is that encryption will only be a small slowdown.

Do you see anything in the log files that looks unusual?

You can use Log File Viewer or look at each of many files. 
One I usually look at first.
 /var/log/dmesg

---

### Post by Fernando Negro on 2013-05-10
Hello there, oldfred.


I'm *very sorry* to be only answering you (and updating this thread) now... But, because this is a shared computer, that I was talking about... Shortly after I made the original post, the (laptop) computer (in question) "went away", for a while, and, not only did I had to wait, for a good time, before getting my hands on it again, but also had to find times when it was not being used by someone else and in which it displayed the mentioned problem.

And, so... I followed your tip and saved 5 different "dmesg" logs, from 5 different times when I caught the computer displaying this strange problem, and I took a look at the logs, only to not find anything wrong in them (no significant error messages of any kind). And, because I was left with no clue as to what might then be the problem, I started looking on the Internet for anyone else who might had been experiencing the same problem, and I managed to find some...

The problem had nothing to do with partitioning. But, it was (after all) a bug in XFCE, in the part that manages the sessions. *(And, apparently, only manifested itself in this particular computer, not because it had encrypted "home" folders, but because it had several user accounts that needed to be managed by this program.)*

[https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791)

So, I downloaded the temporary patch, that is indicated in the bug report, and (after some time using it, I can now safely say that) the computer hasn't displayed that problem ever since.

(Problem solved.)


Concerning the use of the GPT partitioning scheme, in computers with BIOS (that you talked about) I do it because of the extra security I have, when the GPT saves a copy of the partition table, in a second place, in the hard drive - in contrast with the MBR partitioning scheme, where, if (for some reason) the partition table is damaged, "that's it" for the hard drive.


Thank you for your tips.

---

### Post by Fernando Negro on 2013-05-10
(I can't find the "advanced editor", in order to mark this thread as "solved". So, if a moderator can do it for me...)

---

### Post by oldfred on 2013-05-10
My signature has an explanation. New forum does not work fully yet.
Or graphically
 [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Fernando Negro on 2013-05-20
Ah, found it. :)

I can now see the option to edit the thread, in order to mark it as "solved".

Thanks, again, for your tip, oldfred.

---

