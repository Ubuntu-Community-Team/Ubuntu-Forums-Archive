---
title: "Help please. JRE install just messed up FFox"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Chappy7777 on 2008-02-06
I just put in a post about an hour ago about installing the System Updates from upper Rt hand
panel. I downloaded and install 1/2 dozen or so that were there. Nothing I really recognized.

After I let Synaptic install these things all was well. Then I got another flash of red sayin there are 3 more updates. One was JRE6. I clicked install and let it go. It downloaded and installed.

Now, I am on Firefox, everything seems fine. But since I use Gmail for my email, and have been for a year or so. I have it set as my homepage and when I boot up Firefox, it immediately opens my mail for me. problem is. now, when I start, as soon as i can see the inbox, Firefox dies. I am really stuck now. I need my email, obviously.

I went to Applications thing I could remove (maybe, hopefully) JRE6. No go. Can't remove it. 

Please, someone help asap. I have been doing fine until I unstalled this. Ubuntu has been working like a charm. It finds my cable modem when XP can't/won't. I can live w/o the updates 
that I installed today. 

I am running Feisty 7.04 When I open About Ubuntu under System, then click about, I get
Yelp 2.18.1

Help so I can stop yelp. Do I need to do some tweaking to the JRE panel? Please walk me thru then as a NooB if so.

---

### Post by jan quark on 2008-02-06
1.run firefox through the terminal
        - open up the terminal, > accessories > terminal and type in firefox and press enter
          are you getting any error messages?
2. you can try removing jre6 which is sun-java6-jre I guess by running this terminal command:

```
sudo apt-get remove sun-java6-jre
```

if this not help you can however reinstall it again via synaptics

> system > administration > synaptic packet manager
type in sun java into the search field and select for installation the package you want

Besides you don't remember the full name of the update package? But I am quite sure I was java..

let's see

and tell me if your PC has exploded...

---

### Post by Chappy7777 on 2008-02-06
> **jan quark said:**
> 1.run firefox through the terminal
        - open up the terminal, > accessories > terminal and type in firefox and press enter
          are you getting any error messages?
2. you can try removing jre6 which is sun-java6-jre I guess by running this terminal command:

```
sudo apt-get remove sun-java6-jre
```

if this not help you can however reinstall it again via synaptics

> system > administration > synaptic packet manager
type in sun java into the search field and select for installation the package you want

Besides you don't remember the full name of the update package? But I am quite sure I was java..

let's see

and tell me if your PC has exploded...
===========================
I tied everything above except the reinstall thru Synaptic. I don't think the sudo got rid of all the files. FFox is still closing on Gmail. I think due to all the java on there. Tho there is likely java on this "reply" page. 

I tried restarting my PC and running the restore option. It kept asking for a "root password", which I don't have. In the 8 mos or so since I did this install, I have not needed a root PW.
Nor did Ubuntu ask for one to be created during install. All it asks for is an admin PW.

I did create a root PW on Dapper, but I forget the process. I don't know if that would work, but it would be worth trying it if someone can tell me how to create a Root Password. In the terminal...etc I am sure.

is there a way out of this or should I reinstall Feisty. I have Gutsy here, but am afraid to load it due to all the hassles I see people having with it. Feisty has been fine until I messed it up today. Somehow, installing a System Update euchered my browser.

help.........

---

### Post by Chappy7777 on 2008-02-06
Bump

---

### Post by Chappy7777 on 2008-02-06
I really need some help here, or I will have to reinstall 7.04  

Please read the post below to see what happened. Since then I removed and then reinstalled
the Java plugin for Firefox. Everything works fine until I try to play a Flash video or open a my mail site, Gmail.com On those pages Firefox quits. As soon as Gmail's inbox shows, boink, Firefox closes. The page opens ok. 

Same with a site like You Tube. I can go there, but as soon as I click on a video to watch FFox closes.

Some kind of mix up with Java and flash. I am too new to this to know what it is. Would it do me any good to remove FFox and then use Synaptic to replace it? Or is the problem deeper than that.

I don't know anyone where I live (tiny village in Ontario) who is into Ubuntu and could give me a hand. 

Someone in here knows this stuff so please give me some advice.

---

### Post by bwtranch on 2008-02-06
Just got the FF update earlier today. Haven't tried my gmail as I have been on the forum. Let me go check it and I'll get back. Don't bump.

---

### Post by bwtranch on 2008-02-06
I don't have a problem.

---

### Post by bwtranch on 2008-02-06
But, I just run Linux and don't have a bunch of garbage on my machine.

---

### Post by Chappy7777 on 2008-02-06
> **bwtranch said:**
> Just got the FF update earlier today. Haven't tried my gmail as I have been on the forum. Let me go check it and I'll get back. Don't bump.

I don't like "bumping", but I need some help with this, and I don't want my post to end up in the dark area of the twilight zone. I'm not meaning to be pushy or rude. Sorry.

Someone help. 

What Firefox update?

---

### Post by Partyboi2 on 2008-02-06
You could try purging the package which means it will remove the config files as well
```
sudo apt-get remove --purge sun-java6-jre
```

---

