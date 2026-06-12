---
title: "uninstall/remove wine"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by ramona000 on 2008-12-02
Hi guys

I am going mad here..sitting more than 2 hours in front of this pc. I still can't remove wine. i don't know what commands i need to use in the terminal. if i go via synaptic package manager, i have still the menu entry in the applications. can someone help me pleasee?
thx ramona
actually, i am using ubuntu 8.10

---

### Post by Asgar on 2008-12-02
I had the same problem, until i booted into KDE and removed it from there, bang it was gone. No idea why it would only uninstall from KDE but it worked.

---

### Post by ramona000 on 2008-12-02
well....i am not really a genius with pc... how do i boot in kde?

---

### Post by Asgar on 2008-12-04
You have to have KDE install before you can boot into KDE. Use apt-get to install

---

### Post by Happypants on 2008-12-04
Have you given 

```
apt-get remove --purge wine
```

a shot?

Worked fine for me.

---

### Post by stefangr1 on 2008-12-04
> **ramona000 said:**
> Hi guys

I am going mad here..sitting more than 2 hours in front of this pc. I still can't remove wine. i don't know what commands i need to use in the terminal. if i go via synaptic package manager, i have still the menu entry in the applications. can someone help me pleasee?
thx ramona
actually, i am using ubuntu 8.10


I think you did in fact uninstall wine. To get totally rid of everything connected to wine, you can delete the .wine directory, which is located at /home/<username>/.wine  and you can remove it from the menu entry by removing all entries under the "wine" menu by going to the settings panel -> main menu

---

### Post by Happypants on 2008-12-04
:oops:  Looking at the post makes me think I should have read it a bit more closely.  

stefangr1 is right... you may well have uninstalled it already.  

Just cuz you have the packages available in your package manager doesn't mean you actually have it installed on your system.  If the little box next to it is empty then it's not installed.  

My point still stands though... ;)

---

### Post by TyTiger on 2008-12-04
Theres an easy way to get rid of unused menu items from your applications menu. 

*Right* click on the applications menu and select edit menus from the list. 

In the menu editor, scroll down the left pane untill you see a wine fodler, select it and then remove it. 

The application for doing this is quite basic and self explanatory so you should be able to figure out how to use it. ;)

---

