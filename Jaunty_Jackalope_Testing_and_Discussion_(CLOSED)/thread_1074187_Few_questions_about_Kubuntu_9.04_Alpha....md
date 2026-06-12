---
title: "Few questions about Kubuntu 9.04 Alpha..."
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by XtremeGamer99 on 2009-02-18
I've just installed Kubuntu 9.04 alpha on my girlfriends laptop because she was getting sick of Windows XP and it's stupidity. Plus, she wanted to try something new. I told her to pick GNOME or KDE, and she went with KDE because it looks nicer... (can't argue =P)

However, I haven't really used KDE4 too much. My laptop has Ubuntu on it, and my desktop has KDE4, but I never use it (more of a gaming desktop, thus I usually boot into Windows 7). And so I've run into a few roadblocks that inhibit... user friendliness... Since I'm generally new to KDE4, I figured I'd ask instead of muck everything up. I understand that 9.04 is alpha, and I also understand that KDE4 itself is nowhere near 'complete', thus I know that there may be bugs or no solution (right now) to some of these problems...

First things first, I'm not afraid of getting nity-gritty with the terminal to fix anything, nor am I afraid with tweaking config files. Just throwing that out there. =)

1) **KDE Wallet.** This is just plain annoying. Everytime I log onto the laptop, the KDE Wallet opens wanting my login password. It does this because the network manager and Kopete (along with whatever else) is wanting a password that's stored in the wallet in order to start up (ie, the network manager want the WiFi password, Kopete wants the IM password). Is there any way to have the wallet automatically opens upon start-up? Or how about having an 'always open' wallet -- not very secure, but I'm not really looking for security here.

2) **Power Management.** I love the power options in KDE4 However, one thing that I just cannot figure out is what to do when the laptop lid is closed. On GNOME, there is an option to specify what to do if the laptop lid is closed with/without AC power (Nothing, Blank Screen, Suspend, Hibernate). My girlfriend is a heavy 'suspend when lid is closed' person. I can't find such an option for KDE4

3) **Brightness.** This is a small bug. KDE4 recognises all the laptop 'function' keys (ie: Fn + F8 = Volume Mute), except brightness. On the keys, the left arrow depicts more brightness while the right arrow depicts less brightness. However, in practice they are switched: left for lower, right for more (which makes sense, but isn't consisted to what is actually displayed on the keys). How would I fix this minor bug?

4) **Leave Menu.** In the leave menu, Suspend to RAM and Suspend to Disk are given the exact same description ("Pause without logging out"). On top of that, they are worded tricky. I know that "Suspend to RAM" is keeping RAM alive and shutting everything else down and otherwise know as plain "Suspend", and I know that "Suspend to Disk" is writing all data to the disk so that the entire computer shuts down and uses no energy and otherwise known as "Hibernate". The problem is that for people not used to Linux or into computers (like my girlfriend) these two options are very vague and don't seem much different. Is there any way to edit the menu a bit to reword these two options?

There's probably a few more things, but I can't think of them. Thanks! =)

---

### Post by krazyd on 2009-02-19
First, I'd advise you to install the latest *stable* release - 8.10. Especially since your girlfriend is (by the sounds of it) not a linux guru ;). This might take care of issue 1, because I don't see it in 8.10.
2,3: Go to systemsettings, Advanced tab, Power Management.
4: I don't think this can be changed easily.

---

### Post by yther on 2009-02-19
Well, regarding the wallet, you *could* set the password to be blank.  Double-click the wallet icon in the tray (if it's not there, find **kwalletmanager** in the menu or start it with Alt+F2), then right-click the default wallet (usually there's only one) and change the password.  It will complain that your password is insecure, but that's your choice.  :)

You can also answer the prompts when apps want access, and say "Allow Always"; that way (I think) the only prompts you will have to answer are from the wallet manager itself, when it first opens.  In the preferences you can control the time before it closes, or disable the timer so it never closes, once opened.

---

### Post by inportb on 2009-02-19
1) Yeah, try setting a null password **[SIZE="4"]&#8657;[/SIZE]**

2) K > System Settings > Advanced > Power Management

3) Interesting... on my laptop and most laptops I've seen the left button means less brightness. Perhaps you could "fix" the keys by relabeling them ;)

4) This is what education is for... and there isn't even that much to remember. I'm sure your girlfriend isn't like my grandmother who has trouble remembering things sometimes (but if I'm wrong, pardon me).

---

### Post by XtremeGamer99 on 2009-02-19
Thanks for all the replies!

> **krazyd said:**
> First, I'd advise you to install the latest *stable* release - 8.10. Especially since your girlfriend is (by the sounds of it) not a linux guru ;). This might take care of issue 1, because I don't see it in 8.10.
2,3: Go to systemsettings, Advanced tab, Power Management.
4: I don't think this can be changed easily.

As someone who likes 'testing' repositories and alpha/beta releases, I find it hard to *downgrade*. It's a personal vendetta. >_> Besides that, I was set on installing 4.2 rather than 4.1 because of all the improvements in the newer version. Had I installed 8.10, I would have to install 4.2 through unofficial backports and whatnot, and I dislike going that route. 

Thanks for the info on where the laptop lid options are; I must have missed it in the profiles... However, this does not solve the arrow button bug.

Darn.

> **yther said:**
> Well, regarding the wallet, you *could* set the password to be blank.  Double-click the wallet icon in the tray (if it's not there, find **kwalletmanager** in the menu or start it with Alt+F2), then right-click the default wallet (usually there's only one) and change the password.  It will complain that your password is insecure, but that's your choice.  :)

You can also answer the prompts when apps want access, and say "Allow Always"; that way (I think) the only prompts you will have to answer are from the wallet manager itself, when it first opens.  In the preferences you can control the time before it closes, or disable the timer so it never closes, once opened.

I will probably go that route.

> **inportb said:**
> 
3) Interesting... on my laptop and most laptops I've seen the left button means less brightness. Perhaps you could "fix" the keys by relabeling them ;)

Nope, can't relabel them. <_< According to [FONT="Courier New"]xev[/FONT], the left arrow is labeled "XF86MonBrightnessDown" while the right one is labeled "XF86MonBrightnessUp". Is there any way to switch this?

Not that big of a deal, really. But it'll bug me forever.

EDIT:
I just upgraded this morning, and in the upgrade they seem to have renamed the Suspend options to Sleep and Hibernate. All is well on that front. =D

---

### Post by inportb on 2009-02-19
Hm... I just thought of something interesting: [xmodmap]("http://www.x.org/archive/X11R6.8.1/doc/xmodmap.1.html")
And [here's an ArchWiki page]("http://wiki.archlinux.org/index.php/Extra_Keyboard_Keys_in_Xorg") showing you how you might use it. Of course, it may have to be modified for Ubuntu but you get the idea ;)

So for me it would be like... (though my keys behave just fine)
> keycode 232 = XF86MonBrightnessDown
keycode 233 = XF86MonBrightnessUp

(there's also this Input Actions panel accessible from the System Settings app, but it confuses me somewhat)

---

### Post by XtremeGamer99 on 2009-02-19
> **inportb said:**
> Hm... I just thought of something interesting: [xmodmap]("http://www.x.org/archive/X11R6.8.1/doc/xmodmap.1.html")
And [here's an ArchWiki page]("http://wiki.archlinux.org/index.php/Extra_Keyboard_Keys_in_Xorg") showing you how you might use it. Of course, it may have to be modified for Ubuntu but you get the idea ;)

So for me it would be like... (though my keys behave just fine)


(there's also this Input Actions panel accessible from the System Settings app, but it confuses me somewhat)

[FONT="Courier New"]xmodmap[/FONT], that's what I was looking for! I couldn't remember how to reassign keys... Thank you! I will try this out tonight...

EDIT:
Also, I've looked through the Input Actions and Keyboard Shortcuts and everything I could fine in the System Setting, but there doesn't seem to be an option to change the brightness keys via the GUI. Ah well... =)

---

### Post by RIchard James13 on 2009-02-21
New news on the Leave Menu
[http://ivan.fomentgroup.org/blog/2009/02/20/post_42_features_part1/]("http://ivan.fomentgroup.org/blog/2009/02/20/post_42_features_part1/")

---

