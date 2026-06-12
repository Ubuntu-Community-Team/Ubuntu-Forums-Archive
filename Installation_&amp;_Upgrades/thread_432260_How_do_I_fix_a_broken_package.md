---
title: "How do I fix a broken package?"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by Rizlaw on 2007-05-03
Today I tried to install linux printer drivers downloaded from "Brother" for the Brother PT-9500PC label printer. According to the instructions you first install an "lpr" driver package and then a "cups wrapper" package. Being new to this, I really have no clue what they are talking about, I just followed their written instructions to the letter.  Brother's instructions for a Debian (Sarge) driver installation did not work.  I then used Synaptic to completely uninstall the two driver packages I had installed (or so I thought).

Synaptic is now telling me that ** the Software Index is Broken** and that I can no longer install or uninstall _any_ packages (including updates to Feisty) until I fix the problem. The entire list of packages on my computer is "broken" and needs to be fixed. A popup window recommends two options for repair:

_Option 1:_  In a Terminal run: **sudo apt-get install -f**

I tried the first option, it didn't work because the offending driver **pt9500pccupswrapperinch** is no longer located anywhere in the filesystem. More particularly in the folder: /user/local/Brother/pTouch. Therefore, the command to fix and make the repair can not properly complete. I have attached a snapshot of the info returned in Terminal when I executed "sudo apt-get install -f".


_Option 2:_ In Synaptic select the "Broken" filter and mark the offending item for complete removal.

The second option also doesn't work. I get an error that states:

> E;pt9500pccupswrapperinch: subprocess pre-removal script returned error exitstatus 127.

I just spent 2 days restoring this system from another unrecoverable accident after adding a new hard disc to the system. I don't feel like doing this a third time. ](*,) 

Can anyone help? Thanks.

---

### Post by boast on 2007-05-12
bump

---

### Post by lnxconvrt on 2007-05-12
I'm not an expert at it, but did consult the apt-get man page. Small excerpt:
> 
       -f, --fix-broken
Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. Any Package that are specified must completely correct the problem. The option is sometimes necessary when running APT for the first time; APT itself does not allow broken package dependencies to exist on a system. It is possible that a system’s dependency structure can be so corrupt as to require          manual intervention (which usually means using dselect( 8 ) or dpkg --remove to eliminate some of the offending packages).


You may need to use dselect to see if that can resolve the problem. Opening a terminal and doing "sudo su - -c 'dselect'" ought to get you there. Just make sure that you only select the one package for removal. You might have to read the help a bit to figure out how to use dselect, as the interface is not too easy based on the little bit that I have looked at it.

---

