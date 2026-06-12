---
title: "Which Virtual Program To Use?!?!"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by stomponthis on 2007-10-23
I need some advice on which visualization software to use on Gusty.
I have just deleted my partition with XP cause I get so sick of dual-booting and prefer ubuntu.
I have done some research on a these available titles:
vmware
qemu

Could anyone offer me some advice.
I want the virtual OS to run XP with apps like fireworks and dreamweaver and cs3 etc

Thanks

---

### Post by Shazaam on 2007-10-23
There is VirtualBox too.
The thing to remember with virtualization is there is SLIM to NO 3d support so 3d games and such either won't run or run like a slide show.

---

### Post by BoardDWorld on 2007-10-23
I have gone with VirtualBox on Gutsy as I had previously on feisty. It's an excellent program and is easily installed under the Add/Remove Applications. Just select "all available programs" on the right tab then search virtualbox.

I'm currently humming and haring on whether I should use my legal Vista or go with a ripped XP... I know what I would prefer!

---

### Post by stomponthis on 2007-10-23
Sweet! Thanks!
Already installed VirtualBox and am Installing XP.  Guess the best way is to try them all, but really appreciate the feedback! :)
Yeah aggreed with Vista, its a bit of a pain in the you-know-what!
Long Live Ubuntu!

---

### Post by NIT006.5 on 2007-10-23
I also think VirtualBox is the best. That's the only one I've used for the last year.

---

### Post by BoardDWorld on 2007-10-23
Just tested everything and VirtualBox is performing brilliant under Gutsy running XP. For those that don't know you need to add yourself to VirtualBox's user group after it's installed:  


```
sudo gpasswd -a YOURUSERNAME vboxusers
```

---

### Post by Jose Catre-Vandis on 2007-10-23
For a more competent out of the box experience VMware, for more fun and fiddling, and configuration Virtualbox

---

### Post by BoardDWorld on 2007-10-23
> **Jose Catre-Vandis said:**
> For a more competent out of the box experience VMware, for more fun and fiddling, and configuration Virtualbox

Look on the forums! Gutsy just doesn't like VMware. There isn't much fiddling in VirtualBox, nothing out of the ordinary, baby stuff using sliders etc... Are you on Wacky Backy?

---

### Post by LaRoza on 2007-10-23
There is a virtualization forum, it seems to be new, so I am sure you can find useful information their.

As for you question, I don't know, because I have only used VirtualBox, but recommend it because it worked for me. I have no idea how it compares with the others.

---

### Post by Jose Catre-Vandis on 2007-10-23
> **BoardDWorld said:**
> Look on the forums! Gutsy just doesn't like VMware. There isn't much fiddling in VirtualBox, nothing out of the ordinary, baby stuff using sliders etc... Are you on Wacky Backy?

With respect, vmware is only presenting the same issues that it always does after a kernel update, with update or upgrade. Most issues I _have_ read about with regard to vmware on the forum have been resolved.

Virtualbox is not bothered by kernel upgrades. It has generated as many issues with Gutsy from what I can see, but mainly with regard to the interface (qt3 not fully enabled?)

My post was in reference to the ease of use once up and running (e.g. the finer points of getting host interface networking running) which does happen out of the box with vmware. Vbox is still maturing as a product, but its open nature and command line options provide a more techie (geeky) experience.

You have clearly only scratched the surface :)

---

### Post by Jimlas53 on 2007-10-23
I've used VMware for the past couple years, and for the most part, it has worked well.  I have moved over to VirtualBox for about 3 months, and it also works well.  My use is generally limited to a couple of CAD programs that I need to use, and Quickbooks for business purposes.
I really like the seamless display feature in VBox, although there seems to be some ill effect with Gutsy/Compiz.  The upgrade path is much easier with VBox.  VMware is a pain to upgrade, and sometimes the script fails and Synaptic tries to keep installing.
But that's just my experience.  Yours may differ!

---

### Post by stomponthis on 2007-10-26
Thanks everyone for the posts.
Have had Virtual Box up for a few days now running XP and its going nicely :-)
Have read similar issues with VMWare on Gusty aswell !

---

### Post by ldesilva on 2007-10-26
I am using VMWare Server 1.0.4 on Gutsy. no other patch is require. just install xinetd and build-essential and install vmware server 1.0.4

I have another Gutsy running VMWare workstation 6.0.2 build-59824. 

Both my machine is Intel Core 2 Duo with 2GB RAM. All my VMs are stored on an external HDD formatted with NTFS.

---

### Post by GoodPanos on 2007-10-30
Now that we have settled on Virtual Box which one is better the OSE or the closed source?

I am currently using the OSE which is in the repositories of Gutsy Gibbon and it works great but I realized that there is no USB support.

Going off subject here, but could I uninstall the OSE version and install the closed source and use my existing WinXP partition and instance?  Is the closed source easy to install?

---

