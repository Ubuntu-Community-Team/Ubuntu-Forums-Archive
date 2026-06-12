---
title: "Can't log in to 18.04 upgrade at boot"
date: 2019-02-23
forum: Installation &amp; Upgrades
---

### Post by Sleepy-zz-John on 2019-02-23
Hi folks,    Everything seemed to go smoothly with my upgrade from 16.04.2 LTS to 18.04 LTS (which I did on-line) until I tried to boot in to my completed installation for the first time.   Booting took me through GRUB OK and the system started loading up to the point where it needed me to log in.

The log in screen first came up with an orange rectangle showing my username in while characters and a white blank head and shoulders outline on the left.
Below the orange rectangle was a caption 'Not listed?"

But then as soon as I clicked on that orange to move to a password entry field,  I was very briefly (for less than 1 second) presented with a grey entry field saying "authentication error",  quickly followed by a grey screen with nothing but a single flashing cursor at its top left-hand corner.  That screen could only be shifted by a ctrl-alt-del restart.

So no chance to enter my password and get in to do anything on 18.04

I've tried booting again, this time clicking on the "Not listed" caption,  and this gives me a stable grey Username entry field where I can try other usernames and press a "Next" button,  but this only gives me "authentication error" again,  followed by a grey screen with nothing but a single flashing cursor that can only be shifted by a restart

These symptoms make me suspect 18.04 has somehow got itself installed requiring a different username to the one it displays at boot,  but how could I check and /or correct that?

Would there possibly be any way to access, check or change my stored username by accessing files from a LIVE CD??

---

### Post by Sleepy-zz-John on 2019-02-28
Bumping this 'cos in the meantime I've been investigating and found a bit more,   altho basically still stuck unable to log in.

 I can now get in to both a grub terminal prompt from grub's main window and also a root termiinal prompt via recovery mode

I've accessed a list of all the available grub commands but don't really know how to use them

Root terminal prompt shows as "root@TP-L520::~#"  (TP-L520 being my laptop's name Lenovo ThinkPad L520) and from there I can navigate around many of my installed system files, but can't access any personal data.  For example a home folder shows but not the folders it contains.  Also my DATA partition shows but can't access its contents.   That TP--L520 isn't the main system opening  username I remember.  However the same username I remember which  automatically shows when I try to log-in does appear as a folder under /home.

'ls" from the root prompt shows 3 folders:   snap,  core, & current.   Don't think I've ever seen any of these in normal operation.

I did originally burn a LIVE 18.04 LTS DVD from .iso but went for an in-line upgrade instead  because I'm hoping to preserve the apps and settings that were working in 16.04-2 LTS.   I do wonder though whether I could use that LIVE DVD to access my 18.04 LTS files and correct whatever is causing my log-in problem.  Is there a "repair" facility on a LIVE DVD that could handle that without destroying my installed apps & settings?

Would appreciate any suggestions to be in fairly simple step-by-step form since I'm a 77yr old codger with degraded cognitive abilities after chemotherapy..    

    Thanks,      +   John

---

