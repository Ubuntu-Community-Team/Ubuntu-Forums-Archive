---
title: "GeForce FX 5200  graphical issues"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by amberleafguy on 2011-06-12
Hello again

I upgraded to ubuntu 11.04 natty from maverick, in that graphic acceleration worked perfectly until I upgraded, I checked the additional drivers tab and found that the driver is activated but not in use 

current 

NVIDIA accelerated graphics driver (version 173) is installed 

my question is simple if the support is there why doesnt it work for and how can I fix it thanks.

---

### Post by MAFoElffen on 2011-06-12
> **amberleafguy said:**
> Hello again

I upgraded to ubuntu 11.04 natty from maverick, in that graphic acceleration worked perfectly until I upgraded, I checked the additional drivers tab and found that the driver is activated but not in use 

current 

NVIDIA accelerated graphics driver (version 173) is installed 

my question is simple if the support is there why doesnt it work for and how can I fix it thanks.
Stop,,, Don't put a lot of weight on that message, unless your video driver is truly not loading.  (Look at your /var/log/xorg.0.log).

There is a known bug with natty 11.04 and Jockey (the additional drivers applet) where the nvidia driver will be installed and active, but that this applet will say it is "not activated"...

If everything is running fine <> it is working and jockey is just in error.  Even simpler translation of that is > if it's working, don't waste your time trying to make the "indicator" work... that is a known coding problem that other people are working on and will catch up to us in updates.  (ignore it for now.)

---

### Post by amberleafguy on 2011-06-13
Thank you for the information in relation to that. 

So to clarify there is a known bug and it is being patched as we speak?

---

### Post by MAFoElffen on 2011-06-13
> **amberleafguy said:**
> Thank you for the information in relation to that. 

So to clarify there is a known bug and it is being patched as we speak?
On Jockey reporting that a graphics driver is installed, but not activated (when it actually is)? Yes. Known bug being worked on to fix the reporting problem.  Please join that bug as affecting you:
[http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBkQFjAA&url=https%3A%2F%2Fbugs.launchpad.net%2Fubuntu%2F%2Bsource%2Fjockey%2F%2Bbug%2F771788&rct=j&q=ubuntu%20launchpad%20jockey%20driver%20installed%20but%20not%20active.&ei=sw32TfHsNcHjiAKopJ2eBw&usg=AFQjCNF_a4o4uahBATSysFfXY1SIAbwRkA&cad=rja]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBkQFjAA&url=https%3A%2F%2Fbugs.launchpad.net%2Fubuntu%2F%2Bsource%2Fjockey%2F%2Bbug%2F771788&rct=j&q=ubuntu%20launchpad%20jockey%20driver%20installed%20but%20not%20active.&ei=sw32TfHsNcHjiAKopJ2eBw&usg=AFQjCNF_a4o4uahBATSysFfXY1SIAbwRkA&cad=rja")

That is adding a little confusion to people, who either have to verify that the driver is working... or end up needlessly hosing their install while chasing ghosts (trying to fix something that is not broke).

---

### Post by amberleafguy on 2011-06-14
Thanks for the information, I read up about the issue, there seems to be a workaround, however until I am 100% sure it looks like I am stuck for the time being.

---

