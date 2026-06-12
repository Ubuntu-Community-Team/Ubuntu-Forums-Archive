---
title: "Reinstall ubuntu network-manager from cd"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by -=Math=- on 2008-03-28
Hi 

I have a laptop which i installed wicd on, and its not working. To install wicd i had to uninstall the default network-manager, so now i go on the internet..Is it possible to reinstall the default network-manager from my ubuntu cd? 

Thans in advance

---

### Post by zeronothing on 2008-03-28
try this:

open up terminal and enter this into the commandline:

sudo gedit /etc/apt/sources.list

this will open up the repository list and make sure that the top lines that mention something like "deb cdrom:" are not commented out with the "#" character. if the "#" character exists before those two lines then delete the "#" character in front and then save the file by pressing "Save" at the top. next:

execute this in terminal at the commandline:

sudo aptitude install network-manager network-manager-gnome

if that doesn't work try this:

sudo aptitude reinstall network-manager network-manager-gnome

---

### Post by zeronothing on 2008-03-28
also make sure the disc is in the drive at the time. i know this sounds elementary. just wanted to make sure I'm covering my actions

---

### Post by -=Math=- on 2008-03-28
it kinda works, i got wicd uninstalled now, but it tries to download the files from the internet..

---

### Post by zeronothing on 2008-03-28
well, its ok if its downloading the network-manager packages from the internet. this would mean you getting the most up to date version. but if you would like to just install the package from the cd you could comment out every line with the "#" character except for the two with "deb cdrom". then execute the same command from the previous post.

---

### Post by -=Math=- on 2008-03-28
well i dont have internet, so when i get an error when it tries to download the package.

But now you say 2 lines, what 2 lines is it precisely?

---

### Post by zeronothing on 2008-03-28
what distro version are you using? then I could attach a config file to show you better.

---

### Post by -=Math=- on 2008-03-28
i am using Ubuntu Gutsy Gibbon 7.10

---

### Post by zeronothing on 2008-03-28
what I want you to do is open up the repository list and edit it to make it look like the config file I attached to this post:

open up terminal and execute these commands:

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

sudo gedit /etc/apt/sources.list

now look at the config I attached and add the "#" character in front of every line besides the top two lines that do not have the "#" character in front of them.

---

### Post by -=Math=- on 2008-03-28
thanks a lot for the help :)!

But i think i will format it, because it's really ****** up, thinks start to disappear :S

---

### Post by zeronothing on 2008-03-28
sounds like a good Idea. if you need help with anything else post back to the forums.

---

### Post by BloodyLink on 2008-04-29
Hi, I'm new ^^

i have the same problem... and i could'nt fix it... can you explain it again? I don't understand where to put "#"...

I tried to install it but it has no effect... it does not connect!

---

