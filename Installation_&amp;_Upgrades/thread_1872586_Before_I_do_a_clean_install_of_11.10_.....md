---
title: "Before I do a clean install of 11.10 ...."
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by catnip_X07 on 2011-10-30
I have files backed up to separate hard drive.  These files being various word/pdf/music and other files I access often.

What is the fastest and easiest way to backup other files I may need to have a seamless transition back to 11.10 after I install it.  I presume desktop settings are all lost when I do the clean install, in addition to application settings, such as firefox favorites.  Or is the intent of a clean install to wipe out all personalized settings?

---

### Post by 2F4U on 2011-10-31
Yes, that is the intention of a clean install. If you don't like that, you could do an upgrade. However, the risk of failure is more likely if you do an upgrade and part of the problem are personal settings and installed applications.
I install Linux very often on my machines and here is what I do:
- Keep personal data in common places such as Documents, Music etc. in your /home directory
- If I have configuration settings I also keep a copy of them in a special folder in my /home
- Since everything is in my /home, I am able to compress these folders everything into a single archive. Note that I only compress the particular folders I mentioned, not the other stuff that is in my /home folder
- Don't forget to backup stuff like bookmarks to your /home folder. If you use Firefox, thats relatively simple. I do it on a regular basis.

---

### Post by catnip_X07 on 2011-10-31
Where would one find configuration settings for the desktop and bookmark backup for firefox?  Been a while since I've done anything remotely to a new install 

When you say compress into an archive...you are referring to?

---

### Post by oldfred on 2011-10-31
All your user settings are in /home, if you made some system wide settings for wifi or video they will be in /etc. If you have installed a lot of applications you may want to make a list and reinstall them. But Ifound I was reinstalling some that I did not want so I edit the list.

I only have a home system and will do a clean install if I have a major crash. So my backup process is to preserve as much as possible to make that easy.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

