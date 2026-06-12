---
title: "[Gnome 3] Proposed replacement for metacity window decorator: Cowbell"
date: 2009-10-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by shafin on 2009-10-31
Its a css based window decorator, as the developers hope it'll bring web developers into the fold.

You can find more info [here]("http://blogs.gnome.org/metacity/"), as well as the prototype. They have already ported old orange human theme. If you have some experience in css, maybe you can port the new brown human.

---

### Post by autocrosser on 2009-10-31
Very interesting--I was writing themes for Metacity a couple of years ago & this "looks" like a much better direction...

---

### Post by Starks on 2009-10-31
Hmmm. This is quite an interesting development.

I didn't think that CSS was flexible enough to handle this kind of thing.

Anyway, only time will tell if adding more cowbell to GNOME 3 is a good idea.

---

### Post by ronacc on 2009-10-31
reading the link to the cowbell project , this seems to me to be a solution (and an ill concieved one at that ) looking for a problem .

---

### Post by zekopeko on 2009-10-31
> **ronacc said:**
> reading the link to the cowbell project , this seems to me to be a solution (and an ill concieved one at that ) looking for a problem .

care to elaborate?

---

### Post by ronacc on 2009-10-31
the way I read it they are going to take css not use most of it and  "adjust" other parts of it for the purpose of theming the window borders ? I'm sorry I wasn't aware I needed my window borders themed , OH THATS RIGHT I DON"T .

---

### Post by zekopeko on 2009-10-31
> **ronacc said:**
> the way I read it they are going to take css not use most of it and  "adjust" other parts of it for the purpose of theming the window borders ? I'm sorry I wasn't aware I needed my window borders themed , OH THATS RIGHT I DON"T .

I don't understand what you are talking about. 
It's just an upgrade to an already existing infrastructure.

---

### Post by knarf on 2009-10-31
> I'm sorry I wasn't aware I needed my window borders themed , OH THATS  RIGHT I DON"T .
The top of the window is also a 'window border', the one which shows the program title and the buttons (in most themes at least). That border has a certain look and behaviour, as do the other window borders. Those looks and behaviours can vary between themes. This is a way to specify those looks and behaviours in a new-old way which is reminiscent of the way web pages are styled. As to whether this is the right way to go I don't know yet - for lack of studying their proposals - but CSS has shown its merits in web development so it has potential.

I'd suggest having a look at XUL and XBL for these purposes before re-inventing any wheels. If you can design the user interface for a web browser with it it should work for some window dressing as well...

---

### Post by KinKiac on 2009-10-31
> **ronacc said:**
> the way I read it they are going to take css not use most of it and  "adjust" other parts of it for the purpose of theming the window borders ? I'm sorry I wasn't aware I needed my window borders themed , OH THATS RIGHT I DON"T .

So, what you are saying is that you dont use any downloaded themes in your ubuntu at all?  Cause pretty much all of the GTK themes I have seen include window decorations.  There's even a place in compiz just for this.  

Really?  You dont use Emerald or Metacity at all?  Wow.

---

### Post by ronacc on 2009-10-31
considering the state of many web pages the last thing I need is web designers messing with my desktop . I am aware that the top of the window is a "border" containing the program name and buttons , duh . I even customise it to suit my tastes , I do not have the need for any more than that . I am not an "eyecandy" person . I don't waste my time downloading the latest "hot theme" from gmomelook , my dekstop is boringly dull , I like it that way . I am merely expressing a personal opinion .

---

### Post by shafin on 2009-11-01
> **ronacc said:**
> considering the state of many web pages the last thing I need is web designers messing with my desktop .
I don't waste my time downloading the latest "hot theme" from gmomelook , my dekstop is boringly dull , I like it that way .
As you do not download themes, there is very little chance that web developers will be able to mess your desktop. Clearly you are not interested in eyecandy. In that case, this whole development should bring nothing but a 'meh' from you, as you will one of the least affected persons.

On another note, compiz's Jasper window decorator (replacement for emerald) is going to get some love soon, as per developers promise. We are in for some nice new borders.

Using css, how does it affect performance or security?

---

### Post by NCLI on 2009-11-01
> **shafin said:**
> As you do not download themes, there is very little chance that web developers will be able to mess your desktop. Clearly you are not interested in eyecandy. In that case, this whole development should bring nothing but a 'meh' from you, as you will one of the least affected persons.

On another note, compiz's Jasper window decorator (replacement for emerald) is going to get some love soon, as per developers promise. We are in for some nice new borders.

Using css, how does it affect performance or security?
The developers state that they will not release COWBELL unless it's at least on-par with the existing methods speedwise, so no worries there.

---

### Post by Mr. Picklesworth on 2009-11-01
> **ronacc said:**
> the way I read it they are going to take css not use most of it and  "adjust" other parts of it for the purpose of theming the window borders ? I'm sorry I wasn't aware I needed my window borders themed , OH THATS RIGHT I DON"T .

Well, I agree. Metacity's theming should go away and be entirely controlled by the GTK theme engine.

---

### Post by Triggerhapp on 2009-11-01
Im happy with the light weight and boring, when it comes to window decorations. If this doesnt add any latency to drawing the border (I'll be surprised if it doesnt) then I dont care enough to argue against people wanting it.

As it stands, its definatly a fix looking for a problem, imo

---

### Post by zekopeko on 2009-11-01
> **Mr. Picklesworth said:**
> Well, I agree. Metacity's theming should go away and be entirely controlled by the GTK theme engine.

I think they are 2 different engines (GTK and Metacity 3).

---

### Post by gjoellee on 2009-11-01
> **shafin said:**
> Its a css based window decorator, as the developers hope it'll bring web developers into the fold.

You can find more info [here]("http://blogs.gnome.org/metacity/"), as well as the prototype. They have already ported old orange human theme. If you have some experience in css, maybe you can port the new brown human.

So finally I can create themes :p

---

### Post by ranch hand on 2009-11-02
All I can say, as a grumpy geezer, is that they should call it Clara Bell.

Old people will get it.

---

