---
title: "New Installer Slideshow is nice.."
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xArv3nx on 2009-09-04
I just got done burning the Alpha 5 ISO and was pleasantly surprised to see a slideshow while Ubiquity was doing it's thing.

---

### Post by andrewabc on 2009-09-04
Looks ok (from screenshot). Inform users about stuff while installing instead of looking at blank screen with just progress bar moving slowly.

---

### Post by Jesus_Valdez on 2009-09-04
I have photobucket blocked at school, could someone please tell me where I can find screenshots, the wiki, perhaps?

---

### Post by ranch hand on 2009-09-04
The sucker just irritates me.

---

### Post by taavikko on 2009-09-04
> **ranch hand said:**
> The sucker just irritates me.

Why? It doesn't restrict you of anything. 
IMHO good thing to show first time users that few apps are about.

---

### Post by Mr. Picklesworth on 2009-09-04
> **taavikko said:**
> Why? It doesn't restrict you of anything. 
IMHO good thing to show first time users that few apps are about.

Well, in fairness, the title of that F-Spot slide makes me cringe. So, I can see why some may be irritated at the present time. It made sense at one point, then it kind of started devolving for some reason and I haven't fixed it...

There's a wiki page for new content [here]("https://wiki.ubuntu.com/UbiquitySlideshow/UbuntuContent"), and my own rewrite is happening [over here]("https://wiki.ubuntu.com/UbiquitySlideshow/UbuntuContent/DylanMContent").

Thanks for the thread :)

Funny how it has that white border going on. I guess I just finished reading a nice Getting Things Done session in IRC, so, uh... *zap* done! Yay, it looks prettier now!

---

### Post by taavikko on 2009-09-04
> **Mr. Picklesworth said:**
> Well, in fairness, the title of that F-Spot slide makes me cringe. So, I can see why some may be irritated at the present time. It made sense at one point, then it kind of started devolving for some reason and I haven't fixed it...


I was meaning the idea of slideshow during install.
Not to get gaught up on the titles/wording.



(though: relive memories...) = "organize photos with F-Spot" would make more sense to me? but finding the perfect title would require Papa Hemingway :D

---

### Post by andrewabc on 2009-09-04
> **Jesus_Valdez said:**
> I have photobucket blocked at school, could someone please tell me where I can find screenshots, the wiki, perhaps?

[http://www.phoronix.com/scan.php?page=news_item&px=NzUwOQ](http://www.phoronix.com/scan.php?page=news_item&px=NzUwOQ)

---

### Post by ranch hand on 2009-09-04
> **taavikko said:**
> Why? It doesn't restrict you of anything. 
IMHO good thing to show first time users that few apps are about.
I would much prefer to have terminal output to go along with the install or even just the progress bar.

It is not too bad if the Live CD works (A5 doesn't on my box).  You could go do something else.  When using "install ubuntu" you are just stuck with this silly thing.  I doubt that many first time users are installing in this manner but I am sure that to leave this off would take more than I can imagine.

Basically it is probably a personality defect, I just do not like slide shows.  And before you tell me about noobs;
A> I are one.

B> It would have irritated me the first time I ever installed, Hardy last August.

If this blows peoples skirts up that is fine with me.  I just wish there was a way to shut it off and I do not believe that I am the only person like this.

---

### Post by VMC on 2009-09-04
> **ranch hand said:**
> I would much prefer to have terminal output to go along with the install or even just the progress bar.

It is not too bad if the Live CD works (A5 doesn't on my box).  You could go do something else.  When using "install ubuntu" you are just stuck with this silly thing.  I doubt that many first time users are installing in this manner but I am sure that to leave this off would take more than I can imagine.

Basically it is probably a personality defect, I just do not like slide shows.  And before you tell me about noobs;
A> I are one.

B> It would have irritated me the first time I ever installed, Hardy last August.

If this blows peoples skirts up that is fine with me.  I just wish there was a way to shut it off and I do not believe that I am the only person like this.

To each his own, I suppose. I wonder if Alternate Install does this the old fashion way - text.

---

### Post by PGHammer on 2009-09-04
> **VMC said:**
> To each his own, I suppose. I wonder if Alternate Install does this the old fashion way - text.

Indeed it does; it also does not install X (alternate is meant for server and *headless*/X-less installs).

---

### Post by Paqman on 2009-09-04
> **ranch hand said:**
> I just wish there was a way to shut it off

Switch workspaces?

---

### Post by 23meg on 2009-09-04
> **PGHammer said:**
> Indeed it does; it also does not install X (alternate is meant for server and *headless*/X-less installs).

Not really; it installs the exact same set of software as the desktop CD, just with a different installation method.

---

### Post by ranch hand on 2009-09-04
> **Paqman said:**
> Switch workspaces?
This will work fine when we get a CD that the Live function works on.  Having to install, or choosing to install by using the "install ubuntu" option should come with a switch or something to get rid of this thing.

---

### Post by Mr. Picklesworth on 2009-09-04
That would kinda defeat the purpose if it was a switch in the gui... (although, for what it's worth, it will only run if webkit or the ubiquity-slideshow-ubuntu package is installed).

I don't really understand your point, though. Sure, seeing detailed install progress would be great, but that wasn't happening in Ubiquity before and it was never planned to happen in Karmic that I am aware of. The slideshow and detailed install information are not mutually exclusive. They don't even know each other.

---

### Post by Ellipsis on 2009-09-04
I just don't think it is pretty enough. (I guess that matches the rest of default Ubuntu right now...except maybe the splash screen which looks great). But including the slides is a great idea and improvement. Great job guys.

---

### Post by Mr. Picklesworth on 2009-09-04
> **Ellipsis said:**
> I just don't think it is pretty enough. (I guess that matches the rest of default Ubuntu right now...except maybe the splash screen which looks great). But including the slides is a great idea and improvement. Great job guys.

I made a few tiny changes in the source repository. There is no longer a white border (making it look *a lot* less busy) and the arrows are now the ones from the Human icon theme, so they are orange. Let me know if your opinion changes in either direction :)

And it *does* have a pretty cool sliding transition animation.

Here are the after pictures (not from Ubiquity, but close):
[ATTACH]127482[/ATTACH]
[ATTACH]127483[/ATTACH]

Upon switching to the Human theme for the first time in a while, I realize that it doesn't blend with the rest of my desktop like it did using Impression. That's interesting...

---

### Post by kestal on 2009-09-05
> **Mr. Picklesworth said:**
> I made a few tiny changes in the source repository. There is no longer a white border (making it look *a lot* less busy) and the arrows are now the ones from the Human icon theme, so they are orange. Let me know if your opinion changes in either direction :)

And it *does* have a pretty cool sliding transition animation.

Here are the after pictures (not from Ubiquity, but close):
[ATTACH]127482[/ATTACH]
[ATTACH]127483[/ATTACH]

Upon switching to the Human theme for the first time in a while, I realize that it doesn't blend with the rest of my desktop like it did using Impression. That's interesting...

Actually, I really like those attached pics... :) Theme and all.

---

### Post by MadsRH on 2009-09-05
> **Mr. Picklesworth said:**
> I made a few tiny changes in the source repository. There is no longer a white border (making it look *a lot* less busy) and the arrows are now the ones from the Human icon theme, so they are orange. Let me know if your opinion changes in either direction :)


As you might have guessed, I like the white border better ;-)
The new images you posted doesn't have the status text "*creating ext4 file sysrem for...*", which makes it look *a lot* less busy. Removing the border takes something away from the desing - I my opinion.

Although, I think the green arrows also works better for the design, I do agree that it makes sence to use the ones from the Human icon theme.

---

### Post by Mr. Picklesworth on 2009-09-05
> **MadsRH said:**
> As you might have guessed, I like the white border better ;-)
The new images you posted doesn't have the status text "*creating ext4 file sysrem for...*", which makes it look *a lot* less busy. Removing the border takes something away from the desing - I my opinion.

Although, I think the green arrows also works better for the design, I do agree that it makes sence to use the ones from the Human icon theme.

Ah, I was meaning to ask you about the border. Thanks! Looking again, I see where you are coming from.
The problem I have with it is just that, once we throw it into Ubiquity, there are two different borders fighting each other. I guess that frame on Ubiquity's end could be removed, as an alternative...

The reason for the orange arrows is purely because it's consistent with the rest of the desktop's styling. I wasn't sure about nixing the green, since there are indeed distinctive. Still, it may help the colour palette.

---

### Post by Ms_Angel_D on 2009-09-05
Doesn't Karmic Come with Empathy by default & not pidgin?

---

