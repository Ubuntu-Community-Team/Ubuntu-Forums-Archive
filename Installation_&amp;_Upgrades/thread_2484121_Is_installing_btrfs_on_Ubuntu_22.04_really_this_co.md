---
title: "Is installing btrfs on Ubuntu 22.04 really this complicated?"
date: 2023-02-18
forum: Installation &amp; Upgrades
---

### Post by Advait on 2023-02-18
[COLOR=#000000][FONT=Arial]Newbie here.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Ubuntu 22.04 btrfs install video: [https://youtu.be/NYEICTapwy0](https://youtu.be/NYEICTapwy0) I tried to follow this video but it  quickly became super technical. 

Is installing btrfs to Ubuntu 22.04 really this complicated?! 

Way way above my newbie head. Looks like my only option is to hire an online tech support expert. You see any other option?[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]I tried carefully following two other simpler btrfs install videos but didn’t work. One crashed my VM and the other coughed up various fatal errors.[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-02-18
This is a fairly thorough turotrial on installing Ubuntu with BTRFS on root... [https://www.addictivetips.com/ubuntu-linux-tips/ubuntu-btrfs/](https://www.addictivetips.com/ubuntu-linux-tips/ubuntu-btrfs/)

---

### Post by guiverc on 2023-02-18
Lubuntu QA-tests a BTRFS install (*[https://phab.lubuntu.me/w/release-team/testing-checklist/](https://phab.lubuntu.me/w/release-team/testing-checklist/) is a link to our current checklist for 22.04.2 which will be released in a few days*). Selecting BTRFS however is just a drop down item for the basic install we QA test for.

However that's a very simply BTRFS system install that doesn't suit many users  who want specific options for their intended server usage. If you want the power the file-system offers, complexity in options can be required  (If I think about BTRFS, I think of *snapshots*, but the Lubuntu/calamares install doesn't set that up for you with its simple drop-down BTRFS choice).


BTRFS can be simple or complex; depending on a number of factors.  Don't forget Ubuntu offers a number of installers, which you select by which ISO you download an thus use.

---

### Post by Advait on 2023-02-19
> **MAFoElffen said:**
> This is a fairly thorough turotrial on installing Ubuntu with BTRFS on root... [https://www.addictivetips.com/ubuntu-linux-tips/ubuntu-btrfs/](https://www.addictivetips.com/ubuntu-linux-tips/ubuntu-btrfs/)

Yep, this link is essentially covers the same steps covered in this video: [https://www.youtube.com/watch?v=65QGPUSxzZM&t=256s](https://www.youtube.com/watch?v=65QGPUSxzZM&t=256s) I carefully went thru all the steps and didn't work ("Fatal Error: executing grub-install failed...").

Earlier today I hired an online tech support expert to help me get this done. 
---
         So I&#8217;m putting out the request for someone to code up a  simple GUI tool to make it easy for a newbie to install btrfs on Ubuntu  with separate partitions for /, swap and /home. And with all the right  settings like noatime, compress=, space_cache, discard=, etc&#8230;

I want the btrfs setup to unlock the full suite of snapshot backup  features and grub-menu selection capabilities for easy rollback to  previous snapshots of / or /home or both.

Imagine me standing on a rooftop and shouting this into a megaphone.  ;)

My hunch is this GUI tool would be quick and easy to make. Ok coders, get busy!  :P

---

### Post by Advait on 2023-02-19
> **guiverc said:**
> However that's a very simply BTRFS system install that doesn't suit many users  who want specific options for their intended server usage. If you want the power the file-system offers, complexity in options can be required  (If I think about BTRFS, I think of *snapshots*, but the Lubuntu/calamares install doesn't set that up for you with its simple drop-down BTRFS choice).


BTRFS can be simple or complex; depending on a number of factors.  Don't forget Ubuntu offers a number of installers, which you select by which ISO you download an thus use.

As I mentioned in my earlier comment: "I want the btrfs setup to unlock the full suite of snapshot backup   features and grub-menu selection capabilities for easy rollback to   previous snapshots of / or /home or both." My hunch is the basic btrfs install doesn't do all this. Let me know if I'm wrong.

Hopefully the Linux person I hired will get it setup for me.

---

### Post by grahammechanical on 2023-02-19
I find it very difficult to follow video tutorials. I prefer written instructions. The author of the video tutorial referred to in this post likes the sound of his own voice and complicates the matter excessively. The other tutorial when you get past the new user stuff uses a Ubuntu live session to install Ubuntu in a partition that we select to be formatted as BTRFS. It seems much simpler.

I did experiment with BTRFS some years ago. If I remember correctly once we have installed Ubuntu on BTRFS we get an option in the recovery menu called apt-snapshots [revert to old snapshot and reboot]. At the time I was playing with BTRFS all work was done through the command line. Things may have improved since then.

Regards

---

### Post by Advait on 2023-02-20
> **grahammechanical said:**
> The other tutorial when you get past the new user stuff uses a Ubuntu live session to install Ubuntu in a partition that we select to be formatted as BTRFS. It seems much simpler.

Let me know if I'm wrong, but doing it this way only creates the / partition as btrfs. It does not create a separate /home partition as btrfs which I want in addition to the / partition.

---

### Post by ActionParsnip on 2023-02-20
I'd use gparted or the terminal to setup the file systems, then run the installer. Gives absolute control

---

### Post by Advait on 2023-02-20
> **ActionParsnip said:**
> I'd use gparted or the terminal to setup the file systems, then run the installer. Gives absolute control

Yep. I've hired a Linux techie to do that for me.

---

### Post by ActionParsnip on 2023-02-20
> **Advait said:**
> Yep. I've hired a Linux techie to do that for me.

Why? Just plan your file systems. You could even use LVM and extend the file systems as you need. Great time to learn a new skill

---

### Post by MAFoElffen on 2023-02-20
Me, for one, am curious to see what they come up with... LOL. I am always interested about other perspectives on things. And for a new user, why not? I applaud his determination.

One thing missed by many suggestions is that the installer does just a basic canned install, even if you choose btrfs from the partitioner. You can change over to commandline and make many changes for LVM2, BTRFS, ZFS, LUKS2, then back to the installer to install within the framework that is created... This is what I do for ZFS-on-root... But those kinds of things are not for a new user...

But lots of times, instead of just typing away, where any typo can happen, and usually does (getting older), I'll create a script to help myself out. Especially if I am testing with a Filesystem manager and the edge Kernel. That way I can just run the script to set things up for me, then go on with the install. I do that a lot for testing daily builds of Dev Versions. (where I want to see what happens if I do this or that... LOL)

---

### Post by Advait on 2023-03-02
I hired a tech support person and he got Ubuntu installed in VBox with btrfs in the root and home directories. Also installed timeshift-autosnap-apt and grub-btrfs. Now I'm seeing snapshots in the grub menu. Nice! Now I can play around with snapshots before going live.

---

