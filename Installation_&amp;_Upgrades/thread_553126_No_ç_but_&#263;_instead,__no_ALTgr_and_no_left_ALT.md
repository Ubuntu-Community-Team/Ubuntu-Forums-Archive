---
title: "No ç but &#263; instead,  no ALTgr and no left ALT + numpad characters"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by Oceanic on 2007-09-17
I daily have to write French and German,
which means my freshly installed** Kubuntu** Feisty is rather useless.

1   When I type **'+c **it doesn't give the usual **ç**, yet an &#263;

2   Moreover, the** right ALT** key doesn't do anything. Which prevents me to type ß  etc, etc,
    yet, the € sign works

3   Finally, the **left ALT + numpad number** doesn't do anything either (numpad enabled of course)

KEYBOARD Layout settings now are as follows
US English international alt

Seems I am stuck with the limited english alphabet.

This is the common lay-out US En intl layout that I need:
[http://en.wikipedia.org/wiki/Keyboard_layout#US-International](http://en.wikipedia.org/wiki/Keyboard_layout#US-International)

Please help !!! thanks in advance.

---

### Post by jamvegan on 2007-09-17
I do not know how useful this is for you, because I am using Ubuntu (with Gnome), not Kubuntu, so you may not have the same options.  However, I followed the following steps and achieved the results you desire:

1) System->Preferences->Keyboard
2) In Layouts tab:
[INDENT]a) Keyboard Model: Generic 105-key (Intl) PC
b) Click the add button and add: U.S. English International (with dead keys)
c) Check the box next to the newly added layout[/INDENT]
3) Log out and log back in.

I can now type special characters exactly as shown in the link you provided.  That page, incidentally, says to type **Alt Gr+,** to get ç, and that is in fact what I just did.

I hope this works for you! :-)

---

### Post by Oceanic on 2007-09-18
Cheers,
I tried these variations that correspond with the following commands:
setxkbmap -model pc104 -layout us -variant intl
setxkbmap -model pc105 -layout us -variant intl
setxkbmap -model pc104 -layout us -variant alt-intl
setxkbmap -model pc105 -layout us -variant alt-intl

Although none of these offers me deadkeys with the ALTgr (except for €)
which one should in a perfect world be the right one for me?

In other words what is the difference in alt-intl    and   intl   variants?

Where can I find this setxkbmap config file to have a peek?

Thanks again

---

### Post by jamvegan on 2007-09-18
Well, I tracked down my keyboard configuration file for the dead keys variant, but I don't think it will help you, because it's a Gnome XML configuration file.  It would seem that the last two setups that you list would most closely match what I've got.  Also, I believe that your base keyboard configuration is in /etc/X11/xorg.conf.

Hopefully another Kubuntu user who knows how to get this working for you will read this thread.  Best of luck to you!

---

