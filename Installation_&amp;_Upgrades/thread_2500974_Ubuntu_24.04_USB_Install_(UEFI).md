---
title: "Ubuntu 24.04 USB Install (UEFI)"
date: 2024-09-18
forum: Installation &amp; Upgrades
---

### Post by arminimra on 2024-09-18
Hello,
While installing Ubuntu 24.04 via USB in UEFI mode, when it tries to read the USB, I get the following error:
**Initramfs unpacking failed: invalid magic at start of compressed archive**
I have to restart the system. I didn't encounter this issue in previous versions, but I'm facing it in this version as well as related distributions like Kubuntu and the latest Mint. I downloaded the ISO several times and used different tools to create the bootable USB, like Etcher and the built-in USB creator in Ubuntu and Mint, but the issue persists.
Help me!

---

### Post by ActionParsnip on 2024-09-18
Did you verify the ISO you downloaded?

---

### Post by arminimra on 2024-09-18
> **ActionParsnip said:**
> Did you verify the ISO you downloaded?

All Linux distributions based on Ubuntu 24.04, such as the latest versions of Mint and Kubuntu, have this issue. I’ve downloaded them all from their official websites. This problem does not occur in older versions or in other distributions like Fedora or openSUSE, so it cannot be related to verification.

---

### Post by ActionParsnip on 2024-09-18
> **arminimra said:**
> All Linux distributions based on Ubuntu 24.04, such as the latest versions of Mint and Kubuntu, have this issue. I’ve downloaded them all from their official websites. This problem does not occur in older versions or in other distributions like Fedora or openSUSE, so it cannot be related to verification.

The source is irrelevant. The verification ensures the download was complete and consistent. This is why verification is important. A bad ISO will give a bad install experience.

---

### Post by yancek on 2024-09-18
I agree with the comment in post 4 as it is not the source but the transmission from the source to your computer that is in questions.  That does not mean this is the problem but it is always a good idea to verify the download.  Doing an online search for the error you reproted provides a lot of sites dating back several years and they are not exclusive to Ubuntu and derivatives.  Have you done an online searcx and tried any suggested solutions and if so, what were they and what were the results?

Do you get that error or a similar error when you try to boot in Legacy mode if you have that option?  You haven't posted any information on your hardware as to how old/new it is?

---

### Post by arminimra on 2024-09-18
> **yancek said:**
> I agree with the comment in post 4 as it is not the source but the transmission from the source to your computer that is in questions.  That does not mean this is the problem but it is always a good idea to verify the download.  Doing an online search for the error you reproted provides a lot of sites dating back several years and they are not exclusive to Ubuntu and derivatives.  Have you done an online searcx and tried any suggested solutions and if so, what were they and what were the results?

Do you get that error or a similar error when you try to boot in Legacy mode if you have that option?  You haven't posted any information on your hardware as to how old/new it is?


Use your common sense a bit. Do you really think my system only has trouble downloading version 24.04 of Ubuntu-based distributions, from multiple sites with different servers, while all other versions download just fine? Does that make sense? My system is relatively old—about six years old.

---

### Post by ajgreeny on 2024-09-18
Common sense should tell you to do exactly what others have been telling you is the best option, ie, check that the .ISO file you have is not corrupt in any way particularly if you did not download using a torrent client.

Let's face it, it will take you just a second or two to get checksum from the download site of whichever version of the ISO that you have and just another second or two to compare it with the checksum of your downloaded ISO.
I find it very hard to figure out your reason for denying that this is the best thing for you to do at the moment.,

---

### Post by arminimra on 2024-09-18
> **ajgreeny said:**
> Common sense should tell you to do exactly what others have been telling you is the best option, ie, check that the .ISO file you have is not corrupt in any way particularly if you did not download using a torrent client.

Let's face it, it will take you just a second or two to get checksum from the download site of whichever version of the ISO that you have and just another second or two to compare it with the checksum of your downloaded ISO.
I find it very hard to figure out your reason for denying that this is the best thing for you to do at the moment.,


You know, talking to you kinda reminds me of dealing with internet support. Every time you call them up, it’s like they only got one answer: "Just turn the modem off and on again." Man, I’m calling you because I’ve already tried that a dozen times and it didn’t work. I don’t need you to remind me of that!

---

### Post by coffeecat on 2024-09-19
> **arminimra said:**
> I’ve already tried that a dozen times and it didn’t work. I don’t need you to remind me of that!

This is the first time in this thread that you've told those helping you that you've already verified the ISOs. Each time someone advised you to verify the ISO you didn't state that you already had but veered off at a tangent, giving the impression that you were being obtuse. Not knowing that the ISO needs to be verified is common among those seeking help here. You are an infrequent poster, so no one knows how experienced or knowledgeable you are. Effective communication is the key to getting the help you need.

If you really did verify the ISO you downloaded you could have answered, simply and politely, "yes", when asked by ActionParsnip in post #2, "Did you verify the ISO you downloaded?"

---

### Post by arminimra on 2024-09-19
> **coffeecat said:**
> This is the first time in this thread that you've told those helping you that you've already verified the ISOs. Each time someone advised you to verify the ISO you didn't state that you already had but veered off at a tangent, giving the impression that you were being obtuse. Not knowing that the ISO needs to be verified is common among those seeking help here. You are an infrequent poster, so no one knows how experienced or knowledgeable you are. Effective communication is the key to getting the help you need.

If you really did verify the ISO you downloaded you could have answered, simply and politely, "yes", when asked by ActionParsnip in post #2, "Did you verify the ISO you downloaded?"


Y'all's questions are just plain insulting. If you don’t know somethin’, just say so. Don’t be feedin’ me a bunch of nonsense.

---

### Post by coffeecat on 2024-09-19
Thread closed.

@arminimra, before posting again please read and absorb the forum Code of Conduct: [https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

And if you do start another thread, this time answer questions asked you. People are trying to help. Insulting the forum membership gets you nowhere.

---

