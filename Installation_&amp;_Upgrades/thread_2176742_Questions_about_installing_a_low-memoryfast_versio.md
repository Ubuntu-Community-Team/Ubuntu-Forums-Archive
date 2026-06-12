---
title: "Questions about installing a low-memory/fast version like Lubuntu on an old laptop"
date: 2013-09-25
forum: Installation &amp; Upgrades
---

### Post by IAMAcorgi on 2013-09-25
Heyo, hope you guys can help me out.

  
My parents are using my old hand-me-down laptop, a 10 year old  Toshiba Satellite. (They're very computer-illiterate and only use it for  the few things listed below). It's still running like a tank, but  lately has been going super super super slow (both Windows and Firefox).  I reformatted the hard drive and did a fresh reinstall of XP  Professional, but the computer and internet browsing bith still go super  slow and freeze a lot, even after a bunch of speed tweaking that I did.  

  
I was thinking about doing a dual-boot setup for them with XP Pro  along a version of Ubuntu that needs very very little memory. I'm  worried about the laptop's specs (given below) for Ubuntu, but would  Lubuntu still work okay?

  
Also, I've looked at the different types of installations for  Lubuntu, especially for computers with very little RAM, but I can't seem  to figure out the different core installations and ways to install  add-ons afterwards. Anyone know of an easy guide somewhere out there  that guides users through how to install Lubuntu and the different  things afterwards?

  
THANKS!

  [B]
Some more information[/B]

  My parents use the laptop for use it for: 

  
[LIST]
[*]Internet browsing (email, watching youtube videos, listening to audio). 


[*]Google Earth. 


[*]Viewing pictures. 

[/LIST]
  Laptop specs: 

  
[LIST]
[*]RAM: 256MB DDR PC2100 (lower than the original 512mb because one slot went bad). 


[*]CPU: 2.0GHz Intel Celeron 852GM. 


[*]Hard Drive: 40GB

[/LIST]
  
(Also cross-posted here: [http://www.reddit.com/r/Ubuntu/comments/1n54dr/questions_about_installing_a_lowmemoryfast/](http://www.reddit.com/r/Ubuntu/comments/1n54dr/questions_about_installing_a_lowmemoryfast/))

---

### Post by mikewhatever on 2013-09-25
Hate to discourage you, but I think that machine is only good for a week, no GUI headless server. 
256MB of RAM is the major bottle neck, and Lubuntu and Firefox will not run well, unless there is a way to bring it up to 512 at the least.

---

### Post by TenPlus1 on 2013-09-26
You could try installing Bodhi LInux 2.4.0 non-PAE edition as that is what I use on my ancient Compaq M2000 laptop and it works perfectly only consuming 64mb memory on desktop leaving enough for web surfing with Opera (lower memory usage than FF and Chromium for me)...

---

### Post by neyson-v on 2013-09-30
lubuntu is fast but I don't think it will work good in your parents machine. at the moment I'm using 460,3 MB of memory in my 1,5 MB of ram computer. it doesn't mean that your computer won't run lubuntu, I mean, as your computer is less powerful lubuntu won't run certain things to need less memory. if it was my computer I would use debian stable with fluxbox but I don't think fluxbox is good for parents so use lxde instead. 
anyway lubuntu is one of the faster distro so first try it, you can download the iso image and put it into a memory stick then boot the computer an run lubuntu. if it's so slow try debian with lxde.
remember almost any distro with lxde will work better than windows xp anyway, so it's better to try lubuntu than nothing

---

### Post by SeijiSensei on 2013-09-30
Do your parents a favor and have them invest $25 or so in a [1GB memory card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820159408") for that machine.  It will help enormously.  I'd also make sure to allocate at least one or two GB to a swap partition as well.

---

