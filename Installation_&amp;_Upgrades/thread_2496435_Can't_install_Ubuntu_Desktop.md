---
title: "Can't install Ubuntu Desktop"
date: 2024-03-27
forum: Installation &amp; Upgrades
---

### Post by rochense on 2024-03-27
Hi. At first sorry if this has been posted before but I couldn't find an answer on other posts.

I'm trying to install Ubuntu 22.04.4 LTS with dualboot with Windows 10, since I do want to start learning Linux, since I have zero background. I followed the tutorial on the web. However, multiple issues happened.

At first I couldn't even try Ubuntu, since a black screen with letters would appear.

Then I tried to procceed directly to Install in Safe Mode. However, when I reached the screen of Updates it got stuck there forever.

Therefore I did proceed without connecting to Internet and without checking any of the boxes and installing the minimum necessary. It seems to work (I had no issue with the disk partition part) but in the end gets stuck in "Almost finished copying files".

I've also tried flashing my USB (of 64GB) more than once with Balena Etcher and Rufus, none of them seem to work. I have also tried other distribution with similar issues. 

I've been searching old posts to see if it happened before. The ones that I've seen neither understood what a solution could be or did not work for me.

I have a laptop ASUS with a i7-7700HQ and a Nvidia 950m.

Is there anything else I could do? Also the installation is stuck at "Almost finished copying files", can I abort it safely?

---

### Post by Rubi1200 on 2024-03-27
Where are things holding now?

Aborting could be a problem since not only would you have a non-working Ubuntu install but it might also mean not being able to boot into Windows.

Let us know what is going on.

---

### Post by yuralamov on 2024-03-28
No need to set 22.04.4. Install 22.04.3. I started having problems immediately after updating to 22.04.4. Virtualbox stopped working, codeblocks & my progs Nvidia also needs kernel 6.2.0.26. There are more problems here than updating to a new release. I installed 22.04.3 and fixed 6.2.0.26 without hwe. I think the person responsible for the 04.4 release should be fired. It will kill Ubuntu.

---

### Post by yancek on 2024-03-28
>   followed the tutorial on the web

Which tutorial would that be?  Are you referring to the tutorial on the ubuntu site?  If you do an online search for 'tutorial to install ubuntu' you will literally get millions of results.
Did you verify the download of the iso was good?  That is explained at the ubuntu download site.  Is your windows 10 preinstalled on the computer and thus almost certainly an EFI install?  Do you know what EFI is?  You indicate that you began the install and it failed to complete and later say you tried to use Rufus and Etcher and they failed?  Which is it?  Were you able to use some software to write the iso to your USB?  Did you boot and try to install ubuntu in EFI mode.  Can you post a little information on your hardware, particularly how old/new it is?  

If you boot the Ubuntu USB, select the Try option and from a terminal run the following command and post the output her:

```
sudo parted -l
```   

This should answer some of the questions.

---

