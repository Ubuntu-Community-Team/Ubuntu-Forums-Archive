---
title: "sudo apt update FYI"
date: 2021-06-20
forum: Installation &amp; Upgrades
---

### Post by anneranch on 2021-06-20
This post is strictly for information only -  it is provided as service to the community .
No reply is necessary nor expected. 

I was a happy user of 21.04 .
Last night I decided to download new software and did the usual 
"sudo apt update" 
Instead of unusual lines indicating access to "archive "  I received 
string of info basically saying there is no access to the archive...
After reboot the progress report did not look at all as usual
towards the end informing me that my OS partition files were corrupt and attempt was being made to fix it ...

last entry was 
... perform fsck manually  

After doing "fsck" I did not get any replies... 

similar message repeated after each reboot and I have never regained access to "faulty OS ".

None of my "spare" OS would boot - "grub" was always returning back to EFI setup.

---

### Post by Impavidus on 2021-06-21
Then let me tell the community that there's nothing to worry about. Running sudo apt update doesn't mess up your system, but it may do strange things if the system is already messed up. And we all know that an Ubuntu system can be messed up.

I don't see how this post is of service to the community.

---

### Post by coffeecat on 2021-06-21
Indeed. Thanks for your comments, Impavidus.

I think the only service to the community is to demonstrate to less experienced users that a casual association - a series of events that coincide in time - is not necessary a causal one - cause and effect - and that confusing the two denies one the chance of finding a viable solution. All that I can tell from the OP is that there was (possibly) a network issue, and that the filesystem has become corrupted. There are many possible causes for each of those and the update merely exposed the problems rather than precipitating them.

Since the OP clearly doesn't want help for what could be a fixable system, I've closed this thread.

---

