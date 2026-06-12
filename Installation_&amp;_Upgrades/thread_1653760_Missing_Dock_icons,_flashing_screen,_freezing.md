---
title: "Missing Dock icons, flashing screen, freezing"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by elegian on 2010-12-27
Hi,   Yesterday I installed the Ubuntu Netbook Remix onto an hp Pavilion a1320n, as a dual boot alongside 32-bit Windows 7 Ultimate.   

The first issue that became immediate to me is that the docks on the top and left sides of the screen lack icons. On top of that, when you hover over where I suppose icons should be, the black tooltip that comes up is labeled with a white rectangular block instead of telling me what the icon represents. It looks as if the applications function fine regardless of this phenomena; I can click on different parts on the dock and the icons' links still pull up the program with no issue. 

Opening up Firefox, however, led to the screen flashing a colorful pixelated pattern that looks like what happens to an image when you take it into Photoshop and run it through a coarse mezzotint filter. It flashes occasionally while using Firefox, both around the window, on top of the window, and on the entire screen. 

I've also found that I can't run Firefox for more than five-ten minutes without the system freezing on me (mouse won't move, screen doesn't change). 

Any suggestions or ideas would be greatly appreciated! :)

---

### Post by dino99 on 2010-12-27
into a terminal, either:

compiz --replace &
metacity --replace &

about freezing: check driver activation

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by elegian on 2010-12-27
Thanks, I tried the commands above. 

After typing compiz --replace &, I discovered that compiz was not installed, so I installed it. Running sudo apt-get update told me that nothing needed updating, and running metacity --replace & and the other commands did not produce any results.

I should note a few things:
Firstly, immediately after opening terminal, the background was replaced by that  mezzotint pattern I mentioned earlier, and after exiting terminal, I was left with  nothing but the ability to move the cursor.. 
I've also discovered that clicking on certain options in the dock (I can't say which ones - as I've said the text is blocked) makes the screen flash and refreshes the desktop and dock. 
Additionally, when multiple windows are opened, and I click from the title bar of one window to another, the buttons on the left dock flash for a moment.. so they are there, in a sense.. 

Sorry, since I can't see any text or icons in the docks, could you direct me to the driver activation?

---

