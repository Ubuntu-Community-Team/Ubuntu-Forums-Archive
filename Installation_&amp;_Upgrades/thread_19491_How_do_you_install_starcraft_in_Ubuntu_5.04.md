---
title: "How do you install starcraft in Ubuntu 5.04?"
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by Computer Dummy on 2005-03-12
I'm a computer dummy, so don't give me single word answers.  Don't simply say "use wine..." because I don't know what wine is.  I've been a long time windows user but an incident with microsoft have turned me into an anti-windows person.  Any help would be greatly appreciated.  Thanks.

Again, please look at my username.  Don't treat me like some kind of computer genius that could read your mind.  I've been searching this forum and I couldn't understand most of what you guys are saying.

Coincidently, how the hell do you install wine?  I downloaded it but how the hell do you install it?

---

### Post by lyly on 2005-03-12
Wine seems a good solution to me :-). How to install it:
If you are on ubuntu, you can use synaptic (System -> administration -> synaptic) search for "wine" (button in the tool bar) and check the package "wine". you will be proposed to install more librairies, accept (Mark button). Then come the configuration, here I can't tell more without knowing your computer and what you like to do with wine.

Installing starcraft: have to open the installation programm with wine normally a double click in nautilus should be sufficient. If your opengl and graphic driver is ok, you have a chance that it worked on the first try... else post again with the problem you encourted...

good luck :-)

Lynda

---

### Post by Computer Dummy on 2005-03-12
I'm using synaptic but search won't find wine.  I've downloaded it again but it won't find wine.

---

### Post by Computer Dummy on 2005-03-12
Ok, a better question.  Which version of wine do I download?

---

### Post by Kimm on 2005-03-12
ok, this is the way the wine website, describe it.
Open synaptic, then go to Settings -> Repositories and click "New". Then simply copy what it says in this window exactly:

[img]http://www.winehq.com/images/distro/synaptic-repository-binary.png[/img]

then click ok. In the main Synaptic window press Refresh and make a new search for wine

---

### Post by Computer Dummy on 2005-03-12
I feel like I'm being tortured.  The options described are not available.

[IMG]http://img.photobucket.com/albums/v678/GoodIntentions/Screenshot.png[/IMG]

After I click on settings and repositories, I get the following window.

[IMG]http://img.photobucket.com/albums/v678/GoodIntentions/Screenshot-1.png[/IMG]

After I click on add...

[IMG]http://img.photobucket.com/albums/v678/GoodIntentions/Screenshot-2.png[/IMG]

Well?

---

### Post by Kimm on 2005-03-12
](*,) well... if you did it right then I'd have to say Ubuntu has made some changes to synaptic  ](*,) 

but... well, if you realy arnt very good at computers I dont think you shoud use Hoary since its a pre release. I suggest you copy your important files to a CD or something and then reinstall a new Warty system

---

### Post by Kimm on 2005-03-12
oh, btw, running Starcraft in wine will work, but the sound will not work and the game will be realy REALY slow! You'll probably want Cedega to run it.

if you have msn, add me: [email]MrKimm@Spray.se[/email] and well talk some more :razz:

---

### Post by Computer Dummy on 2005-03-12
You are right.  I am now going to install the warty system.

---

### Post by Computer Dummy on 2005-03-12
I don't have msn.  I use aim.  Do you have an aim account?

---

### Post by Computer Dummy on 2005-03-12
[QUOTE=lyly]

Installing starcraft: have to open the installation programm with wine normally a double click in nautilus should be sufficient. If your opengl and graphic driver is ok, you have a chance that it worked on the first try... else post again with the problem you encourted...

good luck :-)

Lynda[/QUOTE]

Again, you are assuming I know what's going on.  Please be more specific.  Where can I find nautilus?  It's not anywhere in my field of vision.

---

### Post by IceAxe18 on 2005-03-12
This procedure would probably be better than going back to warty:

1. sudo gedit /etc/apt/sources.list
2. then add this line:

```
deb http://wine.sourceforge.net/apt/
deb-src http://wine.sourceforge.ent/apt/
```
save your file then exit gedit.

3. In your terminal type:

```
sudo apt-get update
sudo apt-get install wine
```

This should work.  Then your on your own because I don't know how to use wine, but this should get you started instead of reinstalling warty.

---

### Post by Kimm on 2005-03-12
I'm not suggesting he should install warty just for wine, I'm just saying that since he, well, as his name states is a "Computer Dummy" shouldent use a pre release of an OS...

sorry, I dont use AIM...

---

### Post by lyly on 2005-03-13
nautilus is the file browser you can find it in Places -> Computer for example. You can open the cd-rom location, then double click on the setup.exe or install.exe...

---

### Post by Computer Dummy on 2005-03-13
Too late.  I already installed the older version.  I am currently on a road trip from Illinois to Texas.  I'll be back in a week and I will ask you guys about a hundred more questions.  So, be prepared.

By the way, why won't someone that knows how to use wine help me?

---

### Post by Insanely on 2005-03-13
Isn't that what exactly they are trying to do?

---

### Post by Insanely on 2005-03-13
[QUOTE=Computer Dummy]

By the way, why won't someone that knows how to use wine help me?[/QUOTE]

Isn't that what they are trying to do?

---

### Post by Kemotaha on 2005-03-13
Signing up for cedega and point2play might be the easiest to do with out a lot of explaination.  I installed Diablo 2 no problems and heard Starcraft is about the same.  It is $5 a month though.  Better than an evercrack habit.:)

---

### Post by nickless on 2005-08-03
You actually cant use the newest version of cedega, when you want to get starcraft running.

---

