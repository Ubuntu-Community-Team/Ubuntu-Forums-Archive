---
title: "[SOLVED] Sound working in Feisty, but not after upgrade to Gutsy"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by bretto_40 on 2007-10-27
This is driving me insane!  :mad:

Sound and everything was working great in Feisty. I upgraded online to Gutsy, and aside from having to re-install my Nvidia drivers (a necessary evil it would seem), I now find that I cannot enable sound anymore.

I have looked into this as much as I can and I have an Intel 82801 (ICH8 ) on-board sound card.

I have discovered that the real reason why it no longer works is that the Feisty kernel had support for it, but the Gutsy Kernel has had support for it removed!!!

I mean come on... that to me is one of the most frustrating and idiotic things I have ever heard!

Now, instead of the sound just "working" like it did in Edgy and Feisty, it now no longer works and I have found pages online telling me I either have to compile source code into my Kernel or compile an ALSA module.

Aside from this seeming really unnecessary to me when it was working for me just two days ago; I cannot, for the life of me, find a simple, newbie friendly set of instructions on how to fix this issue (including the instructions on ALSA; half of which have command line instructions that don't work).

This is really annoying because not all of us are mind readers or Linux Developers and I often find it hard to get clear concise instructions on how to fix something without being given advice with tons of assumed knowledge that I don't have.

Anyway; sorry for the rant, but I am very frustrated and don't want to go back to Windows which is almost flawlessly easy to install or upgrade. In fact, I'm seriously thinking of switching Distros to something more compatible, but I'd rather stay with Ubuntu because I like Ubuntu.

Can anyone help me to get my sound working in Gutsy?!?!

And also, how do I go about requesting that support for this card is put back into the next release?

---

### Post by bretto_40 on 2007-10-28
For anyone who has this issue I have managed to solve it thanks to some great online support.

The following worked for me:

My card is an Intel 8801H (ICH8 ), anyone who has this card won't get any support for it out of the box in Gutsy, but will in Edgy and Feisty (these are the only two I've tried).

I found this site: [http://users.piuha.net/martti/comp/d630/index.html](http://users.piuha.net/martti/comp/d630/index.html)

The guy who authored this site has posted a script to fix this issue automatically; download the script.

After running the script I had to do the following to get it to work so you may have to do the same:

sudo apt-get install linux-source
sudo apt-get install linux-headers-`uname -r`

Once all of that is done, run the script and the whole process should be done automatically; re-boot and you should have sound again! \\:D/

---

