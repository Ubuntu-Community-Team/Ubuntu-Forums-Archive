---
title: "gnome-control-center"
date: 2010-01-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by KrazyPenguin on 2010-01-20
Where is the gnome-control-center???

I can run it, but can't find it in the menus.

---

### Post by k64 on 2010-01-20
Anything in the System menu was previously accessed by the Control Center. It is accessible in GNOME Shell, however, thanks to $USERNAME > System Preferences.

To install GNOME Shell:

Applications > Accessories > Terminal, then run:

```

sudo apt-get install gnome-shell
```

---

### Post by ranch hand on 2010-01-20
> **k64 said:**
> Anything in the System menu was previously accessed by the Control Center. It is accessible in GNOME Shell, however, thanks to $USERNAME > System Preferences.

To install GNOME Shell:

Applications > Accessories > Terminal, then run:

```

sudo apt-get install gnome-shell
```
Doesn't GM require compositing?  My box (see sig) does not in any way support that.  So this is not a solution for a lot of folks.

---

### Post by uBeer on 2010-01-20
You can right click on the 'Application Places System' thing and then edit the menus. In that screen you can select Gnome control center to show up under 'System' menu.

Edit: I just found out that it's gone from Alacarte (the Edit menu program)... You can always add it yourself, but it's not really convenient...

---

### Post by wipeout140 on 2010-01-20
Also finding it was not available application option in Alacarte, i tried running it from the terminal and it worked and automatically added itself to the menu in Alacarte.

---

### Post by ranch hand on 2010-01-20
> **wipeout140 said:**
> Also finding it was not available application option in Alacarte, i tried running it from the terminal and it worked and automatically added itself to the menu in Alacarte.
Say what?  Where did you find this after running from terminal command?

I read this and thought I better look take a look.  I sure don't see it.

Did you reboot to get this result?

---

### Post by uBeer on 2010-01-20
Me neither, it wasn't there after running it manually. Maybe it's your lucky day :P
Maybe I should check launchpad one of these days to see if there is a report about this...

---

### Post by KrazyPenguin on 2010-01-21
Can't find it either , that's why i started the post.

I do get some errors and warning when trying to launch from a terminal, and then it launches.

There are bugs, i don't know if they are the ones causing this.

Not a big deal though, i don't really use it, was just wondering where it was.
(that's what testing is about, testing things you use and don't use)

thanks

---

### Post by ronacc on 2010-01-21
heres how to get gnome-control-center to show up in the menu.
1 install gnome-control-center
2 in a terminal type gnome-control-center <return>   . it will throw some warnings but start and run ok .
3 click on main menu  ( look and feel section)  select the menu you want it to appear in (I put mine in accesories ) and click new item 
4 enter a name for it , call it whatever you want .
5 in the command box enter  gnome-control-center (or use the browe button to browse to it ) and then click ok .

it will then be available in the menu section you selected under the name you used .

Note! the new item will show up at the bottom of the menu , not in alphabetical order .

---

### Post by ranch hand on 2010-01-21
> **ronacc said:**
> heres how to get gnome-control-center to show up in the menu.
1 install gnome-control-center
2 in a terminal type gnome-control-center <return>   . it will throw some warnings but start and run ok .
3 click on main menu  ( look and feel section)  select the menu you want it to appear in (I put mine in accesories ) and click new item 
4 enter a name for it , call it whatever you want .
5 in the command box enter  gnome-control-center (or use the browe button to browse to it ) and then click ok .

it will then be available in the menu section you selected under the name you used .

Note! the new item will show up at the bottom of the menu , not in alphabetical order .
Well, mine came up in alphabetical order.

---

### Post by ronacc on 2010-01-21
hmm mine didn't , see SS , so I thought I had better add that note.

---

