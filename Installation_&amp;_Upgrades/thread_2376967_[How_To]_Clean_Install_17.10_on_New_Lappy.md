---
title: "[How To] Clean Install 17.10 on New Lappy"
date: 2017-11-07
forum: Installation &amp; Upgrades
---

### Post by pointy2 on 2017-11-07
A brand new laptop w/7th gen i7, 8gb RAM DDR4 (expandable), Intel 620 GPU, SSD, full HD screen with touch, are the main components. I have a  bootable USB ready for the chore. 
This is what I propose it, and any and all advice is appreciated. The firmware and drivers have been updated. 

Clean install of 17.10 to become acclimated for the official 18.04 LTS release. 
Encrypted HD, single volume. 
Burn live USB for another (yet to be determined) OS Mac, Cubes, ect. sometime in future. 
Configure OS with very good security. 

I am wondering about the format of the HD. The install I'm running now, dual boot Win10/16.04 LTS, shows many different volumes in the file system, obviously, Windows takes up a substantial block. 
The uestion is...during install, does Ubuntu auto install the files for the system into separate partitions, or is that configured by the installer (me)? 

Another uestion, about encryption....what would be recommended, full disc encryption, of just the home directory file system? 
What about my driver firmware updates? Will they disappear after install of 17.10?

Excuse my ignorance, but I am....about Linux, anyway. 

All comments and suggestions are welcome.

---

### Post by DuckHook on 2017-11-07
It's best to ask a single question in a single thread. Easier for those trying to help you. However, answers in the order they were asked:

The install process itself has a number of options. You must be careful to select the right one. You can:

[LIST=1]
[*]Automatically wipe your entire HDD and install only Ubuntu
[*]Automatically install Ubuntu only to whatever free space is on the HDD
[*]Manually pick and choose where you want everything to go, which usually goes better if you've pre-partitioned the HDD to place things where you want them.
[/LIST]
Re: encryption--this is not an easy question to answer and involves more questions in turn.:

[LIST]
[*]How paranoid are you?
[*]How important is it for data on this machine to be absolutely secure?
[*]Will you have backups of all data on this machine?
[*]Are you prepared to simply re-install if things ever go south?
[*]
[/LIST]
Recovering a fully encrypted HDD without the original encryption passphrase is basically impossible. This is a double-edged sword: it makes a fully encrypted HDD (if done properly with a high-entropy passphrase) highly secure, but if you ever forget that passphrase, you are hooped. Moreover, if you look back over the threads on this forum over the years, you will find new users who corrupted a fully encrypted HDD either through a bad update, a power outage or experimenting with sudo, and locked themselves out of their computer. A knowledgeable user who remembers their passphrase can usually decrypt such a HDD with a second HDD and a LiveUSB, but such recovery is not trivial.

Therefore, there is no obvious answer to this question. It depends on your answers to the questions above, your risk tolerance, your use case and your willingness to learn some pretty arcane commands should anything ever go wrong. For example, if you are using this machine to carry around highly sensitive patient medical data, then it would be nuts not to encrypt it fully. If this will only be used for surfing and youtube, then full encryption might be overkill and possibly a pain in the neck if things go wrong. Only you know your own use case well enough to decide.

Re: driver firmware updates.

It depends. HW firmware updates actually update the HW itself, so they won't "go away". Software driver updates are often (but not always) part of the newer version, so they may already be up to date. You'll just have to check. However, if you have specialty HW that comes with its own drivers (not part of the repos) then they can't be inherited because you've stated that yours would be a pristine install.

Questions are always welcome but it's best to ask any further ones in independent threads.

---

### Post by pointy2 on 2017-11-08
Thanks DuckHook, for the advice on future posting. Your encryption advice has been received with foresight to my needs, and will study the method to ensure an organized, clean install, so per-partitioning the SSD will have toi be looked in to.  No sensitive medical records, but some BTC trading might be in the works, and aside from writing an expose', nothing of importance to an authoritative agency would be of interest. The entire need for encryption is to remove the 'creep' factor from the obsessed eyes of a stalker who is intent on doing harm. As for the terminal, learning code is needed on this OS and am ready for the challenge.

---

### Post by DuckHook on 2017-11-08
FWIW, here's how I use encryption on my travel laptop (the one I'm using right now).

I don't have anything sensitive on this laptop. The idea is that, on anything that can be lost/stolen, I won't set it up with remembered passwords or user data. The only quasi-sensitive info would be e-mail and cached data from websites. Therefore:

[LIST]
[*]Set up a "private" directory that is encrypted with a good high-entropy passphrase and encryption key.
[*]Move all directories that may have sensitive data into that directory and create symlinks back to where the system expects to find the data.
[*]Encrypt swap.
[*]Redirect /tmp to a ramdisk
[/LIST]
There are a lot of other security measures that can be done for additional hardening, but they have little to do with HDD encryption and can be explored in a separate thread in the security subforum. If interested, please look at the security link in my sig.

This level of security is just right for me. It combines the encryption that I want with the convenience of a working laptop even if something gets corrupted while I travel. At least I can still log in to attempt a fix. However, it has to be acknowledged that it isn't particularly well-hardened. It bears noting that some security gurus on this forum argue quite persuasively for whole disk encryption no matter what your use case. They make good points and it's a legitimate strategy. But keep in mind that they are extremely seasoned users and would not be even breathing hard recovering with a LiveUSB under pretty much any circumstances.

Good luck and Happy Ubuntuing!

---

