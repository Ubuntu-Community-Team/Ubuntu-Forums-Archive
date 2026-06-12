---
title: "Desperately Seeking Help"
date: 2012-06-30
forum: Installation &amp; Upgrades
---

### Post by ltnewbie on 2012-06-30
I am not certain if this is the right forum for this post, but most of my problems do centre around OS installation. As these problems are manifold - though probably interrelated - I think the best way to describe them is by telling the story chronologically.

When, a few weeks ago, I got fed up with Windows, I decided to install Ubuntu. It happened that I had a copy of the installation ISO of version 11.07 mounted to a CD-ROM from a failed Ubuntu adventure a few months ago, so I backed up my files onto USB flash drives and booted from the disk, choosing to wipe out my Windows partitions to install Ubuntu. Things went fine at first - I transferred my files on to the hard drive (and subsequently deleted them on the keys... oops) installed my favourite software, etc. Shortly, though, I found problems downloading and installing and uninstalling and running certain programs, with error codes I did not begin to comprehend. I decided not to panic, though, and rather than try to deal with it all I decided to download and install version 11.10. A problem arose when installing the upgrade, though, and the computer crashed. Now, as it loads, I get this message:

```
the disk drive for / is not ready or not yet present
the disk drive for /tmp is not ready or not yet present
the disk drive for /dev/mapper/crystswap is not ready or not yet present
```When I try to log in, the log in fails and I get this message:

```
Could not update ICE authority file /home/louis/.ICEauthority
```To solve this problem, I again booted version 11.04 from my CD-ROM and installed Ubuntu on to another partition - for those keeping track at home, that makes three: the first one, which I can not log in to; the second, formed during the attempted upgrade, which I can also not log in to; and the third one, installed from the CD-ROM. This third one worked fine - better than the other - and as I slowly came to understand Ubuntu a little more, I found myself interacting with it much more productively. There were problems - Firefox crashed constantly and I couldn't get the hang of converting videos, etc. - but overall things went well. So well that I felt confident enough to again try upgrading to version 11.10. This seemed to go well; the installation was not interrupted and there were no error messages. When the computer restarted and I tried to log in, there was no problem. The problem is that once I log in, I see no GUI, only the terminal. Attempts to launch programs from the terminal indicate that they are not installed.

Here I am: two partitions in to which I cannot log and one without any programs. Obviously, I am writing this on a different computer, but I desperately would like to access my old files and be able to use my old PC. Can anyone help?

-louis

---

### Post by sudodus on 2012-06-30
Welcome to the Ubuntu Forums :-)

I suggest that you get an external hard disk drive (eSATA or USB) and that you backup your personal files onto that drive.

I think that you can access your personal files, when you boot a live session from your Ubuntu CD drive. So use it to backup your files either via the file browser or via terminal commands.

And after that I suggest that you wipe your internal drive and start from the beginning with help from us at the Ubuntu Forums.

So, feel free to ask questions! If I'm not around, there will be other people willing to help.

Good luck!

---

### Post by darkod on 2012-06-30
First of all, the upgrade process doesn't create new partitions, it only upgrades the existing OS keeping the same partitions. How many partitions are there depends on how it was installed. So you have only two installations, not three.

Question: I see you posted a message about cryptswap. In the first install, did you tell it to encrypt your Home directory? Or did you set up encryption of any other kind?

Usually the cryptswap is a sign of encryption.

All of that doesn't matter for the last install you did because they are independent, but it does make a difference if you are trying to copy your data from live mode before wiping the disk and starting all over. You will need to follow instructions for encrypted Home, not the general unencrypted.

So, right now you can boot your last (second) installation but it only boots you into command prompt, right? If you enter your username and password can you login into it?

---

### Post by ltnewbie on 2012-06-30
Thank you both so much for your prompt responses.

sudodus: I have done as you said and used the CD-ROM's trial function, and though the partitions are visible I cannot access their files. The phrase that appears is that I do not have permission.

darkod: I have three partitions; the formation of the second during the upgrade was no doubt the product of further failure to follow instruction on my part. I do not know if I told it to encrypt my home directory, but based on my inability to access the files I suspect I did so in both the first and third partitions. Nothing happens when I enter my user name and password in the command prompt in the third.

---

### Post by darkod on 2012-07-01
If you need to recover data from the encrypted Home, this should help:
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

As for both your installations not working currently, I would download the image of the latest 12.04 LTS, burn a cd at low speed (8x or 10x) from it, and try to boot it into live mode first (Try Ubuntu).

If that works correctly, and after you have copied all data you need from the not working installations, I would reinstall using the whole disk again, this time the 12.04 LTS version.

---

### Post by Kleenux on 2012-07-14
If it can help. I run into the "Cannot update ICEauthority" problem.
The reason was that my home dir /home/me belonged to 'root'...

For some reasons it has been 'chown' to root (and I didn't do it :-). So, a simple 'chown me.me /home/me' fixed the situation.

In this case, it's an Ubuntu in a VirtualBox on a Mac, with "automatic login" (doesn't ask for user/pass at login).
Maybe that's the reason.

Ubuntu 12.04

---

