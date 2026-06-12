---
title: "Ubuntu 12.04.4 runs for a few minutes then becomes unresponsive"
date: 2014-02-27
forum: Installation &amp; Upgrades
---

### Post by South_Canadian_Denizen on 2014-02-27
I have been running Ubuntu 12.04 LTS on my Dell Optiplex 755 desktop and ACer laptop for a year or so with few issues. Both run very well now. I am installing Ubuntu 12.04.4 onto my brother's desktop, wiping out Windows XP, and reconfiguring the partitions all from a bootable USB drive. The install went well. I set up his username and password, installed Gnome shell to replace Unity. The system will boot, let me log in and then it may be (1.) unresponsive to the mouse -or- (2.) Be unresponsive to mouse clicks when I move the mouse to try to do anything (3.) After a few minutes it seems to have some type of GPU issue and reboots to the Password screen. After that it only shows the Unity Background. No task bars at top or bottom of screen. Do I have a GPU conflict with a 9400GT? The on board GPU does not work at all. Any guidance would be appreciated.

Thanks
Southie

---

### Post by Bashing-om on 2014-02-27
South_Canadian_Denizen; Hi !

What processor is the machine running ? How much ram is installed ? 
Now-a-days it takes some horsepower to run the flagship edition ubuntu !
Ya might consider (if the specs are low) to install Lubuntu.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

I personally am impressed as to how well Lubuntu performs on older hardware.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by South_Canadian_Denizen on 2014-02-28
Thanks for your reply Bashing-om,

I don't think the hardware itself is dated. It's a couple of years old.
Biostar MCP6P M2+ motherboard
AMD Athlon 64x2 Dual Core
A bunch of RAM, don't recll how much.

I  believe I have trace the problem to a conflict with Gnome. I uninstalle  Gnome and the system ran for several hours with no problems whereas  Gnome would throw a System Program Problem Detected almost immediately  after login.

Since it ran so well with Ubuntu (which I understand  is aka Unity) I tried re-installing Gnome. This time instead of the  Gnome Shell I installed Gnome Desktop Environment. The problem  manifested itself during install and subesquent re-boots.

I just have to puzzle this out now, why Unity seems ok yet Gnome is not.

Thanks again for your input.
Southie

---

### Post by Bashing-om on 2014-02-28
South_Canadian_Denizen; Hey,

That hardware is well good 'nuff to run ubuntu for sure !

unity and Gnome-shell are reported to co-exist well. Is this the command you used to install gnome-shell ?
```

sudo apt-get install gnome-shell

``` to install the version from the software repository.

We may also want to see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
Maybe think about changing the graphics driver ?

[INDENT]gotta be a cause
[INDENT][INDENT]that we can affect
[/INDENT][/INDENT][/INDENT]

---

### Post by South_Canadian_Denizen on 2014-03-02
Bashing-om, Thank you

Your suggestions fixed my problem perfectly.

As soon I saw your suggestion of updating the drivers I did just that with;
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

I also took your advice and downloaded Gnome from;
sudo apt-get install gnome-shell

instead of the Ubuntu Software Center

I am up and running.
Thanks for your help
Southie

---

### Post by Bashing-om on 2014-03-02
South_Canadian_Denizen; Great !

Pleased you now have a solid system ! And things have worked out .
You did well to recite the steps to resolution.
Please mark this thread solved - 1st post -> thread tools - as this aids others seeking a solution and as well helps keep the forum tidy.

and just
[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

