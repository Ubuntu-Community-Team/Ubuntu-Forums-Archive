---
title: "Right-click event duplication madness"
date: 2009-08-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-08-08
When I right click, anywhere between one and five right-click events fire. It appears to change randomly. Sometimes it works fine. Sometimes it's consistently broken.

I've seen passing mention of this style of behaviour on the forums and IRC but I've never seen a launchpad bug for it yet. Anybody know where I might start looking?

Or even better, anybody know a fix?

Edit: Now on launchpad: [https://bugs.launchpad.net/ubuntu/+bug/410805](https://bugs.launchpad.net/ubuntu/+bug/410805) (I'm subbed to both so I'll see replies to either)

---

### Post by xebian on 2009-08-08
> **OliW said:**
> When I right click, anywhere between one and five right-click events fire. It appears to change randomly. Sometimes it works fine. Sometimes it's consistently broken.

I've seen passing mention of this style of behaviour on the forums and IRC but I've never seen a launchpad bug for it yet. Anybody know where I might start looking?

Or even better, anybody know a fix?

It could be you mouse/finger.

---

### Post by OliW on 2009-08-08
> **xebian said:**
> It could be you mouse/finger.
I'm fairly confident it's not either: same happens with a new wired USB mouse and I've used mice long enough to know when I'm double-clicking. 

As I say, I've seen other people anecdotally reporting similar behaviour.

---

### Post by phenest on 2009-08-08
I've not seen this. If you could determine a pattern, I'll try to reproduce it.

---

### Post by OliW on 2009-08-08
> **phenest said:**
> If you could determine a pattern, I'll try to reproduce it.

I've absolutely no idea what could be causing it, only that it's happening and it's mildly (to put it mildly!) annoying.

---

### Post by tekstr1der on 2009-08-08
> **OliW said:**
> I'm fairly confident it's not either: same happens with a new wired USB mouse...

Sounds more like a hardware issue or double-click speed setting. You've tried this with multiple mice on the same system? Have you adjusted double click speed in the mouse preferences?

---

### Post by OliW on 2009-08-08
> **tekstr1der said:**
> Sounds more like a hardware issue or double-click speed setting. You've tried this with multiple mice on the same system? Have you adjusted double click speed in the mouse preferences?

I hadn't but just for fun, I made the double-click timeout really, really short. The shortest it could be. So short I can barely trigger it if I want to.

But every so often a single right click of my mouse will trigger the test lightbulb.

---

### Post by shafin on 2009-08-08
If you have another mouse nearby, plug that in and test if the problem persists.

---

### Post by OliW on 2009-08-08
> **shafin said:**
> If you have another mouse nearby, plug that in and test if the problem persists.

As I've already said, it does. Different USB bus too.

---

### Post by OliW on 2009-08-08
Some of that anecdotal evidence I was talking about:
[http://ubuntuforums.org/showthread.php?p=7602880](http://ubuntuforums.org/showthread.php?p=7602880)

I'd be more than happy to dig in and find out what's really causing this but I need suggestions (and in some places, probably explicit instructions)

---

### Post by phenest on 2009-08-08
Have you done any testing say, with xev? If not, open a terminal and run xev. A small window appears. Right click in it (not within the black box), and note the results in the terminal. It should be button 3 and the state should change between 0x0(down) and 0x400(up). How many times does it occur each time? There should not be any repetitions, even if you hold the button down.

---

### Post by OliW on 2009-08-08
> **phenest said:**
> Have you done any testing say, with xev? 

I hadn't but I have now.When it breaks, two complete cycles (press, release) fire off at the same time. 

I don't know what more I can tell you from xev's output.

---

### Post by phenest on 2009-08-08
Some one else might know how to take it from there, but all I can suggest now, is to raise a bug report, and give them your hardware specs and the output from xev.

---

### Post by OliW on 2009-08-08
Where do you think I should raise the bug? 

I mean I know it should be on Launchpad, but where? Just under Ubuntu?

---

### Post by ktp on 2009-08-08
Start with ubuntu...if need be other packages/upstreams can be added later.

---

### Post by taavikko on 2009-08-08
> **OliW said:**
> Where do you think I should raise the bug? 

I mean I know it should be on Launchpad, but where? Just under Ubuntu?

[https://wiki.ubuntu.com/X/Reporting](https://wiki.ubuntu.com/X/Reporting)

---

