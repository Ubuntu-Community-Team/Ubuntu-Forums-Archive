---
title: "Problems with Upgrading to Edgy!"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by fazza on 2007-01-03
Hi all, sorry if this is in the wrong place, I'm not really sure where to put it. Got lots of problems after having upgraded directly from Dapper to Edgy, by adding the Edgy repos to Synaptic. Update Manger didn't work.


Firestarter (our Firewall - don't know if you use it, maybe it isn't needed but at least it shows who we're attacked by - 'dedicated**.thehideout.net' seems to be a common one) doesn't always start up. First of all I thought maybe it was because the Session manager wasn't working, but then a pattern emerged - that when the internet wasn't working, it didn't start up. Which brings me on to my second problem. 
    Lately (as in every time I boot up) the internet doesn't connect. I have to unplug the modem from the power and reset it. Then the internet works.
    Thirdly, our gnome-power-manager has gone completely out of the window. I click the log off button, and on it is 'Log Out', 'Lock Screen', 'Switch User', 'Suspend' and 'Hibernate'. Shutdown and restart cease to exist. When they were there, Restart worked, but Shutdown only got as far as the end of the Splash Screen. Then you had to press the power button manually. Now I have created a shutdown button on the desktop so I don't have to type the shutdown command in Terminal. I have been into the Configuration Editor, but there is nothing I can change. I have heard (read) that having Suspend available may not be good for your computer (esp. if it's ours!), so I tried to deactivate it. Not that it works anyway. Also, Switch User takes me to the Locked Screen - there is a button to Switch User on there. I click it, and it gives me the list of users to choose from. I select me (I was logged on as mum previously), and it goes back to the screensaver (which doesn't normally work anyway!).
    Another thing which I haven't actually seen for a long time, because mum is so quick to log on, is the login screen. Last time I saw it, it was the blue one with a yellow flower in the corner (we have it set on random login screen), and none of the buttons were in gtk2.x (is this the right term) style. They were all big, square and grey. Since then, it has always been the same (when I've seen it). So I went into the Login Screen Manager. I clicked it and it didn't open. I clicked it a lot more, and it still only asked me for my password. When I put it in, nothing happened. The command for it is gksu gdmsetup. I think that maybe all the new commands for Ubuntu version 6.10 are different, and the script that was meant to replace them didn't work. The new style of Alacarte Menu Editor had a different command to what it was before, I had to put it in myself. There are a couple of other problems with gdm, e.g. flexiserver and xnest.This would explain the screensaver and the Switch User problems.

I've probably garbled on a bit, but if anyone manages to work out what I've said and can help, please do!
Thanks, fazza

---

