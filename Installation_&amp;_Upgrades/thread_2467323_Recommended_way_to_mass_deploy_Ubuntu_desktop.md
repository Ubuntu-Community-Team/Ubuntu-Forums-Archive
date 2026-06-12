---
title: "Recommended way to mass deploy Ubuntu desktop"
date: 2021-09-23
forum: Installation &amp; Upgrades
---

### Post by jbygden2 on 2021-09-23
Coming from Fedora I'm quite adept at Kickstart for installing desktop machines.

What is the officially recommended way to install multiple Ubuntu desktop machines?

---

### Post by mIk3_08 on 2021-09-23
> **jbygden2 said:**
> Coming from Fedora I'm quite adept at Kickstart for installing desktop machines.
What is the officially recommended way to install multiple Ubuntu desktop machines?

In my opinion, If you are really going to install a Linux Ubuntu Operating System to your
multiple desktop machine. I recommend you should use the Linux Ubuntu Operating System 20.04 LTS
LTS stands for Long Term Support. Actually, It really depends on you which is more convenient to your needs.

---

### Post by TheFu on 2021-09-23
I don't think there is any official answer.  Nobody here works for Canonical.  May want to ask on IRC.

[https://help.ubuntu.com/lts/installation-guide/amd64/apb.html](https://help.ubuntu.com/lts/installation-guide/amd64/apb.html)  Is that not what you seek? It is based on the older deb-install stuff.

A little google-fu found these:
[LIST]
[*][https://ubuntu.com/server/docs/install/autoinstall-quickstart](https://ubuntu.com/server/docs/install/autoinstall-quickstart)
[*][https://ubuntu.com/server/docs/install/autoinstall](https://ubuntu.com/server/docs/install/autoinstall)
[*][https://askubuntu.com/questions/1235723/automated-20-04-server-installation-using-pxe-and-live-server-image](https://askubuntu.com/questions/1235723/automated-20-04-server-installation-using-pxe-and-live-server-image)
[/LIST]


With the removal of python2, many 20.04 and later distributions have challenges in previously working scripts.
There isn't an easy solution for centralized LDAP that doesn't go through MS-AD. If you keep a FreeIPA server, that can still be used or some other openldap manager can work, provided it supports POSIX schemas.

Update:
I just did a server install following the Quickstart.  Did it into a KVM VM (that's my skillset).  I plan to try adding a few packages to the install using the autoinstall.yaml file shortly.  xfdesktop4 will be key, though I don't really use any DEs.  There is a "late-commands" option in the autoinstall file to do the post-install stuff we all like - say putting our ssh keys, bash_aliases, and some extra packages we like or remove some packages we dislike (nano!!!) from the systems.  I haven't tested the autoinstall.yaml yet. Still patching the server install, which had over 200 updated packages.  Think my ISO was from the original server.iso pre-20.04.1.  With your kickstart knowledge, the tftp part should be a breeze - I'd guess.

---

### Post by jbygden2 on 2021-09-23
> **mIk3_08 said:**
> In my opinion, If you are really going to install a Linux Ubuntu Operating System to your
multiple desktop machine. I recommend you should use the Linux Ubuntu Operating System 20.04 LTS
LTS stands for Long Term Support. Actually, It really depends on you which is more convenient to your needs.

Totally unrelated answer to a question that I didn't ask - but thank you for the tip. I had actually already come to that conclusion on my own.

---

### Post by tea for one on 2021-09-23
> **jbygden2 said:**
> Totally unrelated answer to a question that I didn't ask - but thank you for the tip. I had actually already come to that conclusion on my own.

There is no need to berate anyone for trying to help.

Perhaps, it would be helpful to explain:-

What is Kickstart?
What does it do?

---

### Post by grahammechanical on 2021-09-23
i am assuming that these machines are on a network and the network has access to the internet. This information might be useful. I have no experience of putting it into practice. 

[https://ubuntu.com/download/alternative-downloads](https://ubuntu.com/download/alternative-downloads)

> The network installer is also useful if you want to install Ubuntu on a large number of computers at once.

Check this link out under Server and Network Installations. It has links to other documents

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

This link on installing over a local network may interest you.

[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)

There may be easier methods. A more modern tutorial.

[https://www.answertopia.com/ubuntu/installing-ubuntu-with-the-network-installer/](https://www.answertopia.com/ubuntu/installing-ubuntu-with-the-network-installer/)

And this mentions Kickstart

[https://help.ubuntu.com/community/KickstartCompatibility?_ga=2.11427252.1600589099.1632220845-2087616830.1622927185](https://help.ubuntu.com/community/KickstartCompatibility?_ga=2.11427252.1600589099.1632220845-2087616830.1622927185)


Regards

---

### Post by mIk3_08 on 2021-09-24
> **jbygden2 said:**
> Coming from Fedora I'm quite adept at Kickstart for installing desktop machines.
What is the officially recommended way to install multiple Ubuntu desktop machines?
Actually I don''t really get what you mean but if you are after for kickstart then here's the link. below;
[HTML]https://help.ubuntu.com/lts/installation-guide/powerpc/ch04s05.html[/HTML] 
Hope it help.

---

### Post by TheFu on 2021-09-24
> **mIk3_08 said:**
> Actually I don''t really get what you mean but if you are after for kickstart then here's the link. below;
[HTML]https://help.ubuntu.com/lts/installation-guide/powerpc/ch04s05.html[/HTML] 
Hope it help.

Did you mean to point to the Apple solution?  There is another page, linked above, for normal X86-64 systems.  I understand that Apple does things different.

---

### Post by ActionParsnip on 2021-09-24
Could PXE boot with a preseed file setup

---

### Post by mIk3_08 on 2021-09-25
> **mIk3_08 said:**
> Actually I don''t really get what you mean but  if you are after for kickstart then here's the link. below;
[HTML]https://help.ubuntu.com/lts/installation-guide/powerpc/ch04s05.html[/HTML] 
Hope it help.

> **TheFu said:**
> Did you mean to point to the Apple solution?  There is another page, linked above, for normal X86-64 systems.  I understand that Apple does things different.
I don't think I'm sending any apple solution here. It was a link from help Ubuntu website. sorry am I mislaying here?

---

### Post by TheFu on 2021-09-25
> **mIk3_08 said:**
> I don't think I'm sending any apple solution here. It was a link from help Ubuntu website. sorry am I mislaying here?

_powerpc_ is a CPU architecture, like ARM, x86_64, MIPS, Itanium, Alpha/AXP.  It isn't a typical Windows-like hardware in a PC.  While some AIX servers and workstations were built using it, so where Apples, before they changed to Intel x86_64 CPUs.  I think we can still buy Power-based systems from IBM, but I haven't since around 2008.

[https://en.wikipedia.org/wiki/IBM_POWER_microprocessors#Power10](https://en.wikipedia.org/wiki/IBM_POWER_microprocessors#Power10)  shows that the CPU is built on a 7nm process and released in 2021.  My experience was with Power4 and Power5 CPUs.  It was amazing what $2500 could get in a workstation.

The M1 Apple CPU has taken over Macs in the last year.

---

### Post by MAFoElffen on 2021-09-26
I didn't want to answer before... Because I know of "too many" choices to mass deploy, still open for this. I didn't want to muddy up what other's had said and started.

My choices:


[LIST=1]
[*]PXE boot to deploy images from your deployment server. I use Fog Server... Kickstart-like, but with a whole lot of bells an whistles. 
[*]FAI- Fully Automatic Installation. It is a tool for unattended mass deployment of Linux. 
[*]If you are still using the debian installer, then Preseed files. If you are using the new Live Installer, then Live Installer scripts. You can still use either with 20.04. 22.04 will be the Live Installer. (This used to be referred as the Ubuntu Deployment toolkit.) 
[*]MAAS Server. Meant to provide cloud types of provisioning for physical servers, but can be used for workstations. 
[*]Net install to a local server (TFTP Server)... This is Kickstart) 
[/LIST]
 I could go on...

---

### Post by mIk3_08 on 2021-09-26
> **TheFu said:**
> _powerpc_ is a CPU architecture, like ARM, x86_64, MIPS, Itanium, Alpha/AXP.  It isn't a typical Windows-like hardware in a PC.  While some AIX servers and workstations were built using it, so where Apples, before they changed to Intel x86_64 CPUs.  I think we can still buy Power-based systems from IBM, but I haven't since around 2008.
[https://en.wikipedia.org/wiki/IBM_POWER_microprocessors#Power10](https://en.wikipedia.org/wiki/IBM_POWER_microprocessors#Power10)  shows that the CPU is built on a 7nm process and released in 2021.  My experience was with Power4 and Power5 CPUs.  It was amazing what $2500 could get in a workstation.
The M1 Apple CPU has taken over Macs in the last year.
Thanks a lot for the information TheFu. This helps me a lot. Thanks for sharing. It was really a brilliant information.

---

### Post by TheFu on 2021-09-26
> **mIk3_08 said:**
> Thanks a lot for the information TheFu. This helps me a lot. Thanks for sharing. It was really a brilliant information.

I'd found that link too and skipped over the "powerpc" part as well.  As I was skimming it, something just seemed a little off and different from my experience - then it clicked - Apple!  I did a different search and found the links that I eventually posted.

BTW, I setup a quick batch install (as I said above) and it worked.  I did an xubuntu install and that worked too. The trick in my method following the quick-guide was to provide the minimal boot stuff at machine boot and have it get the full ISO from NFS.  I'm not a fan of using tftp. tftp has zero security and is easily hacked.

MAFoElffen's post is real-world, hands-on stuff.  Since my setup is under 20 systems in a single building, the effort to go with some of those just isn't worth the effort.  The OP never said the number of systems or any logistical information, so we don't know if a 10 min of effort answer or a 2-person, full-time, for a month, is reasonable.  I've had to deploy 25K laptops at work before.  We ended up using FedEx and shipping the systems to the vendor for re-imagining when they broke. Our image was applied before they were delivered to our 1200+ locations as well.  Because they were field, hardened, laptops, the systems would get abused.  A few got run over by trucks after being left on the roof of a vehicle - that was the story. We'd ordered 10% more than needed just to be available for swaps while systems were being fixed after breaking.  

Anyway, there are lots of ways to address these things.  Desktops in a school are different from 10K desktops in a University and those are different from 50K desktops in 10 countries around the world.  Getting the image deployed really isn't the hardest part. Keeping them patched, secured, maintained, and preventing "stupid user tricks" is harder, IME. At least with Linux, most of those things aren't nearly so hard when they are networked.  Anyone who has tried to patch that "other desktop OS" knows how nearly impossible it is.  50% of the problem is actually getting them patched. The other 50% is being able to report accurately that they ARE actually patched.  We hopped to have 90% of the systems patched within 7 days of a new patch being pushed. Sounds easy, right?  Users do unexpected things, even when you remind them "don't turn off your PC tonight".  50% will anyway.  Hard to patch a system that isn't on.

---

### Post by mIk3_08 on 2021-09-27
> **TheFu said:**
> 
MAFoElffen's post is real-world, hands-on stuff.  Since my setup is  under 20 systems in a single building, the effort to go with some of  those just isn't worth the effort.  The OP never said the number of  systems or any logistical information, so we don't know if a 10 min of  effort answer or a 2-person, full-time, for a month, is reasonable.   I've had to deploy 25K laptops at work before.  We ended up using FedEx  and shipping the systems to the vendor for re-imagining when they broke.  Our image was applied before they were delivered to our 1200+ locations  as well.  Because they were field, hardened, laptops, the systems would  get abused.  A few got run over by trucks after being left on the roof  of a vehicle - that was the story. We'd ordered 10% more than needed  just to be available for swaps while systems were being fixed after  breaking.
What a great and amazing experience. I like it. This is not an ordinary. I haven't encounter this experience yet in Linux. I mean it, I start to learn computing using other OS the common one the MS OS and I experienced a lot. I did not deny it. But when I encountered  the Linux when I was still in school way back when I'm in college 20 years ago maybe, I was amaze with Linux Red Hat that time. My experience of Linux is very different from the other OS. It was exactly 101% turned around. with full total package that other side OS can't overrate it. By the way it was very cool. And thank you too for sharing new ideas to the post. I mean it, It help a lot TheFu. 

> **TheFu said:**
> Anyway, there are lots of ways to address these things.  Desktops in a  school are different from 10K desktops in a University and those are  different from 50K desktops in 10 countries around the world.  Getting  the image deployed really isn't the hardest part. Keeping them patched,  secured, maintained, and preventing "stupid user tricks" is harder, 
You are exactly right TheFu. This is actually depends to the end users. The users can make it better or brake it in just a few blink of an eye. :-) It will totally messed up. 

> **TheFu said:**
> Anyone who has tried to patch that "other desktop  OS" knows how nearly impossible it is.  50% of the problem is actually  getting them patched. The other 50% is being able to report accurately  that they ARE actually patched.  We hopped to have 90% of the systems  patched within 7 days of a new patch being pushed. Sounds easy, right?   Users do unexpected things, even when you remind them "don't turn off  your PC tonight".  50% will anyway.  Hard to patch a system that isn't  on. 
hahahaha :-) Also this one, this actually on the end users. We can't just say that it was their fault its just that they just don't know what they have done. And its actually very important things to do.

---

### Post by SeijiSensei on 2021-09-27
I believe you might be looking for this:  [https://landscape.canonical.com/](https://landscape.canonical.com/)

---

### Post by jbygden2 on 2021-10-15
> **SeijiSensei said:**
> I believe you might be looking for this:  [https://landscape.canonical.com/](https://landscape.canonical.com/)
No, that comes later - after installation.

---

### Post by jbygden2 on 2021-10-15
Ok, I've tried preseed - and ended up with additional questions: [Install extra packages with preseed]("https://ubuntuforums.org/showthread.php?t=2467953")

Any takers?

---

### Post by MAFoElffen on 2021-10-16
I have looked at that post/thread... and asked which of the two threads should I try to explain this... 

I think you deserve an explanation of how it works. That will not work with just creating the file. (I guess that from your other comments there.) It will not work with the graphical installer. There is a way that you have to tell it to use the file, from within the text mode of the installers.

---

### Post by jbygden2 on 2021-10-18
Yeah, continuing this in the other thread [Install extra packages with preseed]("https://ubuntuforums.org/showthread.php?t=2467953")

---

