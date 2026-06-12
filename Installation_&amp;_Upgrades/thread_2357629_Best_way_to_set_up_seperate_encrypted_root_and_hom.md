---
title: "Best way to set up seperate encrypted root and home partitions"
date: 2017-04-04
forum: Installation &amp; Upgrades
---

### Post by Richard_Romick on 2017-04-04
Greetings.  I am hoping you can give me some advice on my installation plan.

I am attempting to install Ubuntu on an 128 GB SSD while having home on a separate 500 GB SSD.  Since this is on a laptop, I would prefer to have root and home encrypted.

Initially, I tried to use custom partitioning with no avail.  I tried to set up /home on a encrypted physical partition on the 500 GB SSD.  However, when I tried to continue setup, it kept saying it couldn't mount the drive.

Instead, I thought I might have the system automatically install everything encrypted to the 128 GB SSD while also turning on home directory encrypting.  Then, I would move my home directory to the 500 GB SSD using commands like:

(where $HOME and $USER are placeholders for actual values)
ecryptfs-umount-private
  rsync -avP $HOME/$USER/.Private $HOME/$USER/.ecryptfs /new_mount_point/$USER
  rsync -avP $HOME/.ecryptfs /new_mount_point

and then updating fstab to mount the 500 GB SSD to home.

All of that to ask you, would this work well?  Would I have the 500 GB to use for my home directory, encrypted?  Are there any potential downsides? Would it be ok for me to use my computer for a while with home @ 128 GB SSD and move home to the 500 GB SSD at a later date?  Thank you for your time.

---

### Post by DuckHook on 2017-04-05
> **Richard_Romick said:**
> &#8230;All of that to ask you, would this work well?  Would I have the 500 GB to use for my home directory, encrypted?  Are there any potential downsides? Would it be ok for me to use my computer for a while with home @ 128 GB SSD and move home to the 500 GB SSD at a later date?  Thank you for your time.
You're asking a number of separate questions, albeit all related to one another. From what I can read between the lines, you want to separate out your /home because you want to back up the data on it separately to your root?

If so, then it is not necessary to separate out /home. You may be better off leaving /home under root on your 128GB SSD and just separating out your data onto your 500GB SSD. You could then encrypt this data directory and symlink the files/subdirectories back to /home. This way, you don't have to deal with the secondary decryption of /home which is where your auto-decryption seems to be choking. This has the added advantage that, come time to upgrade, you can upgrade your whole install (including /home) without having to touch your data. Just make sure that you access your data using *autofs*&#8212;not *fstab*&#8212;and you should be able to have the encryption service activated prior to your disk being accessed. It's this sort of improper sequencing that often causes the problems you've been experiencing.

---

### Post by Richard_Romick on 2017-04-05
I actually came across this help.ubuntu.com article yesterday when I was doing some additional Google searching.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

It was very helpful.  I managed to move my home directory the way I wanted.  I don't know about what you said about symlinking verses moving home, but I finished it before reading your post.  Based on your experience level verses mine, I will probably regret my decision, but it is what it is.

---

### Post by DuckHook on 2017-04-06
> **Richard_Romick said:**
> …Based on your experience level verses mine, I will probably regret my decision, but it is what it is.Please don't be swayed by experience level. You should do what is most suitable for you, and if it works, you're good to go and should just celebrate. :KS

In the strange world of computing, experience has its limits.

Good Luck and Happy Ubuntuing!

---

