---
title: "Gutsy Upgrade with NVIDIA card"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by mikecoal on 2008-02-21
I recently upgraded to Gutsy and now when i boot it freezes at around 25% of the way through and stays there till i reset.

I have an nVIDIA GeForece 5200 that worked fine with Fiesty on my Duel Boot win Vista / Ubuntu.

I am able to boot fine using the onboard card but when i switch back to the PCI card in the BIOS and reboot, it hangs.

I tried several of the kernels to see if it made any difference and i couldnt see any change.


 i installed the Envy utility but when i ran it (with the on board card obviously) it complaind that my system wasnt the right type of system and aborted.

---

### Post by jan de beuker on 2008-02-21
You could try this 
Put envy in you /home directory
When you see the grub menu press escape
Select the second option (recovery mode)
You will end up in a root terminal install envy  
After that use this command envy -t
Envy will then run in text mode

Jan

---

### Post by mikecoal on 2008-02-21
I can not boot in recovery mode using the NVIDIA card, it freezes.
If i boot to recovery mode using the onboard card i get the following error in Envy.

ENVY ERROR: Your operative System does not seem to be supported by ENVY.

---

### Post by jan de beuker on 2008-02-21
That is strange because grub is your bootloader there is nothing started yet.
Then  I have not a clue how your graphics card can be the course of this 

Jan

---

### Post by jan de beuker on 2008-02-21
Can you still boot in Vista ?

---

### Post by jan de beuker on 2008-02-21
In that grub menu is also a recovery mode isn't it ?
Because pressing escape is only neccessary to enter the grub menu

---

### Post by mikecoal on 2008-02-21
it loads to the grub loader just fine and yes there are selections for recovery mode. When i hit enter it proceeds to load to a certain point then freezes.

 When i boot to vista it loads fine.
 When i boot using the onboard graphics card, it works fine.

Of course i have to switch between PCI and Integrated in the BIOS each time i do this but that dosnt seem to be an issue.

---

### Post by jan de beuker on 2008-02-21
Sorry can"t help you 
When you select recovery mode and it still freeze's I don't understand that because as far as I know no graphics drivers are loaded.


Jan

---

### Post by mikecoal on 2008-02-21
That is what i thought as well. It shouldnt even load the xorg.conf until you actually load the gdm right?

Since it hangs even under recovery mode, wouldnt that suggest a hardware or kernel issue?

---

### Post by jan de beuker on 2008-02-21
Don"t know your card works fine in Vista and Ubuntu works good with your onboard
But I know also that upgrade can cause strange effects so you could try installing gusty with a cd no update


Jan

---

