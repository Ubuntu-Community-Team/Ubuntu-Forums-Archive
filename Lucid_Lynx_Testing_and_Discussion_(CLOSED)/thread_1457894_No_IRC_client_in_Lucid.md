---
title: "No IRC client in Lucid?"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kirk M on 2010-04-19
I know this might sound like a stupid question but was the IRC chat client removed from Lucid for a reason? I originally installed Lucid Beta 2 which has since been regularly updated and I just now went to use the IRC client (XChat wasn't it?) and realized it was missing. Not including an IRC client by default seems a bit unusual.

---

### Post by MacUntu on 2010-04-19
I'm pretty sure Xchat wasn't part of the default installation the last couple of releases.

Edit: Maybe you can use Empathy: [http://live.gnome.org/Empathy/FAQ#How_can_I_connect_to_IRC_in_Empathy_.3F](http://live.gnome.org/Empathy/FAQ#How_can_I_connect_to_IRC_in_Empathy_.3F) (I never tried).

---

### Post by Kirk M on 2010-04-19
> **MacUntu said:**
> I'm pretty sure Xchat wasn't part of the default installation the last couple of releases.

Edit: Maybe you can use Empathy: [http://live.gnome.org/Empathy/FAQ#How_can_I_connect_to_IRC_in_Empathy_.3F](http://live.gnome.org/Empathy/FAQ#How_can_I_connect_to_IRC_in_Empathy_.3F) (I never tried).

Thanks for reply. I could have sworn that XChat was included in 9.04 and 9.10 as I used it on a regular basis and I don't recall having to install it. And yeah, supposedly you can use Empathy as long as "telepathy-idle" is installed. No bother though, I'll just install XChat from the "new and improved" software manager. Sheesh, how dare they make me waste less than a minute of my time! :lolflag:

---

### Post by Joeb454 on 2010-04-19
I'm not sure XChat has ever been included in the default packages. Pidgin used to be, maybe that's what you were thinking of?

As you say, it's easily installed :)

---

### Post by TuckLive on 2010-04-19
Konversation was in 8.04 by default right?  When did they take that out?

---

### Post by Seren on 2010-04-19
> **TuckLive said:**
> Konversation was in 8.04 by default right?  When did they take that out?

Konversation, QT4/KDE4 version, was not ready for Jaunty IIRC, and it was replaced by Quassel, another QT4 based IRC client.

Since then, I think Konversation has become the default KDE client again. So it was probably removed for one or two release.

---

### Post by philinux on 2010-04-19
There's no chat client installed in lucid only the gwibber social client, which I have no use for currently.

Empathy was the default in karmic which is not that user friendly for IRC. 

Pidgin is very user friendly for IRC or xchat and also chatzilla firefox addon.


[edit] Empathy must have got removed from my install during an update. Must do a clean install soon!

---

### Post by phillw on 2010-04-19
pidgin is either love it or hate it, I fall into the love it catagory as it offers me a 'one-stop' shop for my IRC, MSN, Yahoo! and AIM. It's not as polished or as functional as some dedicated apps, but it's a good little all-rounder.

Regards,

Phill.

---

### Post by 23meg on 2010-04-19
XChat was last included by default in Breezy (Ubuntu 5.10).

---

### Post by IndyGunFreak on 2010-04-19
> **Joeb454 said:**
> I'm not sure XChat has ever been included in the default packages. Pidgin used to be, maybe that's what you were thinking of?

As you say, it's easily installed :)

Xchat-Gnome was for a while I do believe..but I don't recall seeing it installed "out of the box". since around 7.04-7.10.. I think Pidgin is a great IM client.. not so great for an IRC client.

IGF

---

### Post by jpeddicord on 2010-04-19
> **philinux said:**
> There's no chat client installed in lucid only the gwibber social client, which I have no use for currently.

Empathy was the default in karmic which is not that user friendly for IRC. 

Pidgin is very user friendly for IRC or xchat and also chatzilla firefox addon.

Actually, Empathy is still in the default install. It's on the messaging menu and in Applications > Internet.

---

### Post by Slorg on 2010-04-19
I'm pretty sure Pidgin has been replaced since 9.10 (Maybe even since 9.04)
Empathy is the new standard IRC client, it's still there...

---

### Post by andrew.46 on 2010-04-20
And of course the best of all of them, irssi, is a simple:
```

sudo apt-get install irssi irssi-scripts
```

away from you :).

Andrew

---

### Post by gunksta on 2010-04-20
Using Empathy as an IRC client appears to have one major problem - it doesn't alert you when someone talks to you. It highlights the text in red, but I don't see any way to make it flash, shoot off fireworks, or other wise let me know that someone wants my attention.

Empathy does a good job of telling me when someone wants to chat via Jabber, but not IRC. 

I wound up installing irssi, xchat and some new toy called smuxi. Smuxi is a mono app, but it's built like Quassel. It has a core AND a client. Thus, I could run the core on my box at home, which is never disconnected from the 'net and use the client to connect to this core from my various laptops, netbooks, etc. It's like using irssi + screen.

---

### Post by brucewagner on 2010-04-21
Just use Synaptec to install:    xchat

No?

---

### Post by Yellow Pasque on 2010-04-21
> **brucewagner said:**
> Just use Synaptec to install:    xchat
No?
Well, of course, but I don't think that was the OP's point...

---

### Post by gunksta on 2010-04-21
I think this discussion - and the notion that a Linux system should come with an IRC client by default - fits well into what Jono is getting at here.

[http://www.jonobacon.org/2010/04/21/ubuntu-power-users-community/](http://www.jonobacon.org/2010/04/21/ubuntu-power-users-community/)

This is, after-all, his point. Power-users (like many of the folks on this forum) are an important cause/reason for Ubuntu's success and Ubuntu can't afford to lose us. But, Bug #1 can't be solved with IRC clients and other past notions of what defines a distro. 

Thus, Ubuntu removes XChat, etc. and replaces it with Empathy which is honestly a lame IRC client. But, if I want something more I know what to do and I don't mind. But, when my girlfriend tried to start XChat on our shared netbook - it proved Mark's point. XChat (or any other dedicated IRC client) has no real place on a mainstream system. She had no idea what she was doing and wasn't interested in learning.

So, I deleted XChat and left it with irssi and empathy if I'm too lazy to do anything else.

---

### Post by Longinus00 on 2010-04-21
> **gunksta said:**
> I think this discussion - and the notion that a Linux system should come with an IRC client by default - fits well into what Jono is getting at here.

[http://www.jonobacon.org/2010/04/21/ubuntu-power-users-community/](http://www.jonobacon.org/2010/04/21/ubuntu-power-users-community/)

This is, after-all, his point. Power-users (like many of the folks on this forum) are an important cause/reason for Ubuntu's success and Ubuntu can't afford to lose us. But, Bug #1 can't be solved with IRC clients and other past notions of what defines a distro. 

Thus, Ubuntu removes XChat, etc. and replaces it with Empathy which is honestly a lame IRC client. But, if I want something more I know what to do and I don't mind. But, when my girlfriend tried to start XChat on our shared netbook - it proved Mark's point. XChat (or any other dedicated IRC client) has no real place on a mainstream system. She had no idea what she was doing and wasn't interested in learning.

So, I deleted XChat and left it with irssi and empathy if I'm too lazy to do anything else.

Exactly, power users can install their own favorite irc client so they don't need one to be installed by default.

---

### Post by vininim on 2010-04-22
> **gunksta said:**
> Using Empathy as an IRC client appears to have one 
I wound up installing irssi, xchat and some new toy called smuxi. Smuxi is a mono app, but it's built like Quassel. It has a core AND a client. Thus, I could run the core on my box at home, which is never disconnected from the 'net and use the client to connect to this core from my various laptops, netbooks, etc. It's like using irssi + screen.

Interesting, this smuxi client seems to do what irssi2 wants to. Empathy should aim at something like that.

---

### Post by gunksta on 2010-04-22
Exactly. Smuxi and Quassel are both interesting tools and I think it is important that open source tools continue to develop distributed cores and clients, in a manner similar to many command line tools, but with the added benefit of a distributed "cloud oriented" manner.

---

### Post by daas88 on 2010-04-22
I think xubuntu is the one which has xchat out of the box.

---

### Post by gunksta on 2010-04-25
I want to revise my opinion of empathy as an IRC client. It's not perfect. In fact, it's not even all that great, but apparently I was flat out wrong about one thing. Empathy DOES give me a pop-up/indication when someone is talking to me directly on IRC.

It looks like the earlier build of empathy I was using had a bug in it and was failing to do this, but this bug has since been corrected in Lucid.

The disadvantage of using empathy is a real lack of flexibility. I can't write out a list of custom words to flag for, etc. "Advanced" IRC features are lacking, but it works a peach for basic stuff on this netbook.

---

