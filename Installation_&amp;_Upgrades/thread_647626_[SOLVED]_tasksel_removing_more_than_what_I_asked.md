---
title: "[SOLVED] tasksel removing more than what I asked?"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by AaronLS on 2007-12-22
To try installing lamp, on Ubuntu desktop 7.04 I used:
sudo tasksel

I checked lamp, and didn't change anything else(only other thing checked was the ubuntu desktop).  It froze on 0% when installing, and I left it for awhile and eventually got some sort of apt-get error, I think it mentioned error (255).  So I rebooted the system, because I was having some weird problems earlier, and thought it was related.  After rebooting, I SSH'd in, and tried sudo tasksel again, this time lamp was already checked, and hitting enter just closed the menu.  So I figured I would uncheck it, close the menu, then open tasksel again and check it.

So now after unchecking LAMP and hitting enter, it is now removing a huge amount of things,one of the first things I noticed it said it was removing was:
"Removing ubuntu-desktop ..."

WTF!?  I didn't touch that selection.  Now it's be going on for about 20 min uninstalling stuff.  I'm afraid all the work I've done on this thing is getting flushed down the toilet!

---

### Post by AaronLS on 2007-12-22
Well after it finished uninstalling everything. I ran sudo tasksel again, and both items were no longer checked.  So I checked them both(ubuntu desktop, and lamp) and hit enter.  This was the result, it's been on the blue 0% progress screen for about 20 minutes:

Extracting templates from packages: 100%                                              
Moving old data out of the way
Package configuration                                                                     
                                                                                          
                                                                                          
                                                                                          
                                                                                          
                                                                                          
                                                                                          
                                                                                          
                                                                                          
                                                                                          
                                                                                          
                                                                                          
                                                                                          
                                                                                          
                                                                                          
 âââââââââââââââââââââââââââââââââ¤ Installing packages âââââââââââââââââââââââââââââââââ[17;Please wait...                                                                          â                                                                                     â  
 â                                                                                     â  
 â                                                                                     â  
 â                                          0%                                         â  
 â                                                                                     â  
 âââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââ

---

### Post by AaronLS on 2007-12-22
It finally finished with this:

tasksel: aptitude failed (100)   

So I'll try to find out what that error code means in the meantime, but if anyone has any ideas in the meanwhile I'm open ears.

---

### Post by AaronLS on 2007-12-22
I rebooted and I was left at the login prompt.  So I logged in and ran:
sudo apt-get install ubuntu

Seemed to go smoothly.  I rebooted, but after rebooting there was an error during boot up saying that X Server could not start, and said something to the effect of it not being setup properly.  I chose ok, and am back at the shell.  I viewed the logs and it says no driver found, unable to find module 'nvidia'.

I don't know what to do now.

---

### Post by AaronLS on 2007-12-22
Well I saw a suggestions related to XServer problems.  And since I was just about ready to give up on this and reinstall Windows, I figured it couldn't hurt.  I ran the below and chose all the default options, then ran sudo reboot and it booted into ubuntu desktop finally.  Also before this I tried(without success) "sudo aptitude reinstall ubuntu-desktop" or something like that, because I saw something where someone said aptitude was better at checking dependancies than apt-get.  So ultimately the below fixed the issue, but it may have also been dependent on the reinstall command as well.

sudo dpkg-reconfigure xserver-xorg

---

