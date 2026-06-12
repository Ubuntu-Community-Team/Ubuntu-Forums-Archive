---
title: "dvdrip not triggering cpu to scale it's speed up"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jerome1232 on 2008-10-27
I just starting using dvd::rip .98.6-0, 8.10 2.6.27-7-generic (and rt I just forgot to change my grub so I'm in generic right now) x86_64 amd64 3700+@2.4ghz and I noticed it was transcoding at 4-6 fps, horrible especially for 64bit which is supposed to go fast at this.

Well then I turned on my frequency scaling applet and noticed my cpu is staying at 1ghz while dvdrip is trasncoding, doing anything else (opening a new window, uncompressing a file, starting a game) will trigger the upscale to 2.4ghz. 

For testing I turned off scaling in my bios and dvdrip now goes 15 fps which is a vast improvement, I'm ripping at really high quality settings so I figure that's an okay speed for me.

Does anybody have any insight as to why it wouldn't trigger my cpu to scale it's speed up? (perhaps this is a dvdrip issue I'll start testing more apps once this session is complete)

---

