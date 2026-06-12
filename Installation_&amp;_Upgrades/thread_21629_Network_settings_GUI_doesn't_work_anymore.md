---
title: "Network settings GUI doesn't work anymore"
date: 2005-03-23
forum: Installation &amp; Upgrades
---

### Post by Suolx on 2005-03-23
Weird thing, suddenly Network settings GUI doesn't work anymore.
First it asks password (sudo) and when it starts the GUI it says "The entered password is invalid. Check that you typet it correctly and that you haven't activated the "caps lock" key. 

Password IS correct. If I enter different password at the beginning, it says that:
"Failed to run network-admin as user root: Wrong password"

It's a shame because otherwise Ubuntu hoary preview is working really nice on my Fujitsu-Siemens amilo v2000 laptop. Suspend/Hibernate etc. 

Any ideas?

---

### Post by acascianelli on 2005-03-23
try removeing the file .gksu.lock in your home folder.

---

### Post by Suolx on 2005-03-23
I removed it but it didn't help and it keeps coming back :I

---

### Post by acascianelli on 2005-03-23
see if gksu is working at all, try running 'gksu firefox' or something...itll as you for the root password just like the network config would.

i noticed a few days ago that there was a few updates for gksu thru synaptic.  maybe there is a bug fix in a newer version you could install too.

---

### Post by Suolx on 2005-03-23
gksu firefox works ok...tho not with user password but only root?
network-admin doesn't start even with root password or root desktop...
Updating the hole system, tho I have bad

---

### Post by Suolx on 2005-03-23
Great...updates broke X...
dmesg says 
mtrr: base(0xe8020000) is not aligned on a size(0x300000) boundary
mtrr: 0xe8000000,0x8000000 overlaps existing 0xe8000000,0x400000

---

### Post by Suolx on 2005-03-23
Solved, configuring new packages wasn't completed so fonts were missing =)
Still no go with the network-admin...everything else seems to be working fine.

---

### Post by Suolx on 2005-03-23
Okay, continuing my monolog...

It was PPP config that messed up the panel...works now =)

---

### Post by Behel on 2005-05-11
First post here!
And first of all, congratulations to everybody who make this community so great! I have installed quite succesfully Ubuntu on an old Sony Vaio PCG-F707.

Coming back to the subject of the thread, I have exactly the same problem, I enter my username password for the System->Administration->Networking, the gui loads then a window tells me that my password is invalid (and I know it is correct).

Suolx, you seem to have manage to solve the problem, how? What is PPP config? I am connected to my university network, so no ADSL for me.

Thanks for all

Loic - UK

---

### Post by Behel on 2005-05-12
Me again...

I noticed more problems that I did not manage to resolve with the forum and which can be all linked:

- In addition to  System->Administration->Networking, I cannot access also System->Administration->Users And Groups, System->Administration->Share Folders and System->Administration->Time And Date. It is the same problem i.e. after typing my CORRECT password, it loads the GUI and then show this message in a window:

"The entered password is invalid
Check that you typed it correctly and that you haven't activated the "caps lock" key"

I then have to click on "Close" and the GUI vanished... What is annoying is that after, if I want to start again, it doesn't not ask me for my password anymore but simply loads the GUI and then the previous message.

---

### Post by selevent on 2005-09-22
same thing i have with trouble Behel,
what must i do ?

---

### Post by DaveBr on 2005-09-29
I have the exact same problem as Behel. I enter the correct password for the default (only!) user but seemingly don't have access. After it's failed once I don't even get the password screen anymore - it just falls into a black hole.

Same for all of the administration GUIs I've tried......

Could someone be kind enough to explain, in newbie friendly terms, how I might solve this little bug-ette??

Thanks.

---

### Post by Behel on 2005-10-05
Hi,

I solved my problems a few months ago so I don't really remember how I did it. But I certainly remember that I was fed up and finally decided to reinstall a fresh version of Ubuntu. And now it works really fine. What I can say is that one have to be carefull when creating the accounts and configuring the network card. For example I wanted to have a different hostname than the one proposed (I am on Windows network in a university) and this is probably where some of my problems came from. During the reinstallation I took the hostname given by my network. Also avoid to create a root account...

That's all I can say unfortunately... Since the reinstal, everything works fine!

---

### Post by Behel on 2005-10-05
Just to make clear the last point about not creating a root account:
[http://ubuntuforums.org/showthread.php?t=71904](http://ubuntuforums.org/showthread.php?t=71904)

---

