---
title: "Unable to increase screen brightness"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by taffy-nay on 2007-07-10
I have been playing about with the 704 live cd and have found that I am unable to increase the scree brightness on my vaio laptop (a "VGN-C2S" if you were wondering).

Other function key combo's work fine.

Enyone else found this?

---

### Post by Odrodzona-Sarmacja on 2007-07-10
> **taffy-nay said:**
> I have been playing about with the 704 live cd and have found that I am unable to increase the scree brightness on my vaio laptop (a "VGN-C2S" if you were wondering).

Other function key combo's work fine.

Enyone else found this?

yep! :D

Gamma correction do not apply or sticks in KDE or GNOME gui. It is officially known gnome&kde gui bug in ubuntu.

Only Xubuntu gui doesn't have it. Xfce gamma works. So first you need to install xfce desktop on ubuntu or kubuntu, then log into xfce session and then using xfce desktop/display settings for brightness and gamma correct whatever is to correct. Gamma/brightness changes should hopefully stick in ubuntu, when logging again to the other two desktops.

---

### Post by taffy-nay on 2007-07-10
That certainly seems like quite a ghastly workaround.

If that is the case I might as well JUST use Xfce.:-|

---

### Post by Odrodzona-Sarmacja on 2007-07-10
> **taffy-nay said:**
> That certainly seems like quite a ghastly workaround.

If that is the case I might as well JUST use Xfce.:-|

That's also what I use as my primary desktop and that's also why I do so :D

When you finished with installing xubuntu you would also like to install "kdebase" desktop or "gnome-core(I'm not sure how this package is called)" package. This way you can still enjoy on xubuntu your current gui (it is optional gui-session choice during login) and still enjoy and use your favorite apps you like from your current gui in xfce gui ;)

---

### Post by taffy-nay on 2007-07-10
I'm not to sure about using Xfce though, i've not used it before and I'm not really into the whole "learning curve" thing. I like things to just work.

If I do use Xfce, will Compiz Fusion work ok?

---

### Post by Odrodzona-Sarmacja on 2007-07-10
1. open synaptic package manager
2. select "xubuntu-desktop"
3. install it
4. log out
5. choose in options in loging screen "xfce session" and log in
6. change applications->settings->display settings/desktop settings
7. log out
8. log in into your gui

9. If that kompiz of yours doesn't work then "->synaptic package manager -> find "xubuntu-desktop" -> completly remove -> apply".

It is not harder then so :D , but are you brave enough man to do it? If not, then plz ask your girlfriend to do it for you ;)

---

### Post by taffy-nay on 2007-07-10
That seems easy enough and the sarcasm has been duly recieved :-D

I though xUbuntu was a dirivative of Ubuntu that included Xfce and that Xfce itself was a window manager that could be installed seperatly through a package manager?

I'm still a little miffed as to why the two most popular window managers don't handle gamma correction correctly (if at all)

---

### Post by Odrodzona-Sarmacja on 2007-07-10
> **taffy-nay said:**
>  I though xUbuntu was a dirivative of Ubuntu that included Xfce and that Xfce itself was a window manager that could be installed seperatly through a package manager?

I was thinking myself exactly like that just 1 month ago. :D

Now I know there are these 5 gui packages:
1 GNOME (Ubuntu)
2 bare & basic GNOME
3 Xfce (Xubuntu)
4 KDE (Kubuntu)
5 bare & basic KDE

Only 1,3 and 4 are official ubuntu distributions. They all are also just software packages you can install like that on your ubuntu. However only 2,3 and 5 come without these milions of annoying programs, which you never heard about and you can be sure never to use in your life.

> I'm still a little miffed as to why the two most popular window managers don't handle gamma correction correctly (if at all)

In this forum you can find also section dedicated specially for xfce, gnome and kde guis issues. Ask nice people over there. I know only it is a bug ;)

---

### Post by taffy-nay on 2007-07-10
Well, thank you for all your help.

I think I may take a gander at the section you suggested :-D

---

