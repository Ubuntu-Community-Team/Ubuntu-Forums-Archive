---
title: "[SOLVED] Explain Please...."
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by newuserincalgary on 2008-11-18
Will someone please explain to me why running the update manager on a working Ubuntu 8.10 install causes the system to completely fail and stop booting at all (even manually).

Is this a normal Linux thing?

Is this something I should expect all the time using Ubuntu?

I have spent a day and a half searching all sorts of threasds in the forums and posting some threads myself in addtion to this one, all with very little help.

The closest thing I can figure out is that something in the upgarde process changed something in the initrd pkg and now it won't read from the ext3 partition.

Do I have to live in fear of ever doing system upgrades? (assuming I can even get it working again....)

Am I too much of new Linux user to have anyone bother to respond to me....?

What gives....?

---

### Post by Keen101 on 2008-11-18
ummm.... i'm going to say that's not normal.

My 8.10 system works fine.

 You did mean 8.10 right? or are you upgrading from 8.04?


also, you could try posting in the absolute beginner forum. Most posts get multiple replies there...

---

### Post by newuserincalgary on 2008-11-18
Wow....there is someone out there...thanks

I did a clean install of 8.10 x64....first time linux install ever for me

which seems like part of the problem...if I had installed 8.04 first like I was going to, then i would have had an alternate system to boot into which would likely allow me to try and fix the 8.10 upgrade problem....unfortunately the live cd doesn't let you do to much as far as I can tell...

I will try the other forun thanks again

---

### Post by Idefix82 on 2008-11-18
I don't quite understand what you mean by "the live cd doesn't let you do much". What you can try to do for example is boot from the live cd, see what changes the recent updates have done and try to revert them. Also, have you tried booting into recovery mode? Does that work?

To actually answer your question in this thread:
1. It is not normal that an upgrade introduces a kernel panick and it happens very rarely but it is nothing out of the ordinary. You have to remember that, the system being free, there is little paid testing going on before updates are released to the public. Thus, Ubuntu relies on the testing being carried out by the community. With such a serious problem as yours, I am sure that if it's the update's fault then there must be other people experiencing this and it will be fixed.

2. It is unreasonable to write 2 posts within 12 hours and then start flaming. You have to give people time to reply. Not everybody is online all the time and not everybody reads every thread immediately. Here, it is considered polite practice to bump your thread every 24 hours. If that doesn't help for several days, then start bumping more often.

3. No, you are not too new to be replied to, only a tad too aggressive.

4. Personally, I don't install every update if I know that I won't have time to sort out any problems that may occur. However, it is very advisable to install the updates which are marked as essential security updates. The most risky thing are kernel updates but you are always offered the option to keep your old kernel also and to have a choice at boot. If you only want to be notified of the security updates you can adjust the settings in the Synaptic Package Manager under the "Repositories" menu.

---

### Post by Keen101 on 2008-11-18
Yeah the other guy is right. Be patient. I remember when i posted my first question i was very jumpy too. I thought people were ignoring me. But, it turns out they were not, but i did have to bump once.

Yeah, have you tried booting an old kernel. Chances are you have more than one option in your GRUB menu, and an older one should work fine.

Also, recovery mode might work.

The live-cd is actually pretty useful sometimes. Sometimes it needs an activated root, but that can be achieved with 'sudo passwd root'.

---

### Post by newuserincalgary on 2008-11-18
Ok....sorry about my frustration....i just saw all these other threads getting replies right away....i am new to this

in response to some of the suggestions...

i do not have another install to boot into....i only installed 8.10 from the live cd

recovery mode booting does not work...i get the same error message

i do not know how to undo the upgrade....

running sudo from the live cd does not seem to let me do an update on the initrd file....

---

### Post by newuserincalgary on 2008-11-18
Further responses...

I have booted from the live cd...how do see what the recent changes are....how do i try and revert them?

the update manager did not seem to give me the option of keeping the old kernal when it did the upgrades....should i be using something else other the the update manager to do the updates?

---

