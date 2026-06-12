---
title: "Using virtual magnifying glass?"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by bloodshot13 on 2010-10-28
I have ubuntu 10.04 and I installed a package "virtual magnifying glass" that I saw on another post.- [http://ubuntuforums.org/showthread.php?t=628741](http://ubuntuforums.org/showthread.php?t=628741). I've gone in Assistive technologies(enabled assistive technologies)>Preferred Applications>Selected GNOME Magnifiyer without screen reader(I guess this is the program I downloaded) and enabled run and start.. I restarted my computer but I don't see a magnifier? Hope this post is clear as I am new to ubuntu. Any help would be appreciated. :)

---

### Post by bloodshot13 on 2010-11-08
I've found that I can run vmg in terminal but I have to keep term. open to use it. Is there a way I can keep vmg on my panel w/o running it w/ term.?:-\" I use this program to read articles whilst I sit back in my chair. When I'm using vmg(looking at articles,news, ect.) it sometimes crashes ubuntu and starts back to login!? Think maybe my processor or video card is not capable of handling such a program?

                          
                         description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz                                                      
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
 description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz

---

### Post by robsoles on 2010-11-30
Hi-ya, sorry I didn't stray across your thread sooner, I've been distracted.

You can make a command continue and release the command line by invoking it in the background. Assuming the command is vmg;```
user@ubuntu:~$ vmg &
```Will make it start and persist, until you use whatever it has to stop it, beyond the terminal window closing (provided your desktop session doesn't end either). It's possible to stop it from the terminal but that shouldn't be necessary.

Being that you've taken 10.04 you could right click the menus (upper right corner on clean install of 10.04) and choose "Edit Menus" and use the dialog box that opens to add the magnifier to available programs from the menu.

If you already solved it then well done but otherwise, sorry again that I've turned up late :)

---

### Post by bloodshot13 on 2010-11-30
First of all,thanks for the reply. I used vmg & and I get this:screenshot.


Vmg comes out on screen but when I close term. it goes away. When I right click on top right menu it gives me.........about..........remove from panel............and lock to panel.

---

### Post by robsoles on 2010-11-30
Sorry, on a clean install of 10.04, using gnome, it's in the upper left hand corner and there is also a 'Main Menu' item under the 'System'->'Preferences' menu that opens the same thing.

When I ran:```
gksudo nautilus &
```in terminal, before posting above, I was able to close the terminal and continue to browse as root using nautilus so the instance of nautilus I called from the terminal, and the privileges escalation I called for from the same terminal, didn't get closed or revoked after closing the terminal - I really do expect that if you put an '&' on the end of the command it will persist when terminal is closed.

**Don't include the '&' for the menu-item I suggest you create.**

Please confirm that you are saying you put ```
vmg &
```into terminal and the magnifier closed when you closed the terminal?

---

### Post by bloodshot13 on 2010-12-02
When I run :
vmg &
         It shows the screenshot term. and the vmg icon is in the top panel on the right. When I close term. the icon goes away.

---

### Post by robsoles on 2010-12-03
That's odd but never mind it now - what about the menuitem method?

---

### Post by bloodshot13 on 2010-12-04
> **robsoles said:**
> That's odd but never mind it now - what about the menuitem method?
  I don't see the menu item vmg anywhere...I'm not sure where the program is...I see orca magnifier under universal access but I don't want that because I had some serious problems with it before as when I went to login to ubuntu it would magnify so large I couldn't do anything. It took me a while to fix that problem.

---

