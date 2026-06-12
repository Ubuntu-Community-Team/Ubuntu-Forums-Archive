---
title: "could not retrieve bsdutils..."
date: 2004-10-21
forum: Installation &amp; Upgrades
---

### Post by Mighty Mik on 2004-10-21
it has a net connection, and a disk burned in Linux, and i STILL can't get it to install. Ok...i do have a known, good 'iso , so what parameters an i missing to get a good burn? what mirror archive for the installer incase it stuffs the cd install. Hopefully pressed cds will arrive sometime before christmas...

---

### Post by chadskinner on 2004-11-06
I'm having the same problem.  I'm using the ISO Power Toy in Win XP and no matter what I do I get the same message about BSD Utils.  I checked Bugzilla and someone reported a bug but no one really looked into.  I don't understand why you can burn the ISO on some platforms but not others.

I now know of at least 3 people having this problem.

I'm going to try burning the ISO on one of my Linux systems and I'll post a reply here to let you know if it worked.

---

### Post by chadskinner on 2004-11-06
Okay, I'm an idiot for not reading all the posts firsts.  Looks like someone else has done what I was going to do and it worked.

[http://ubuntuforums.org/showthread.php?t=804&highlight=bsdutils](http://ubuntuforums.org/showthread.php?t=804&highlight=bsdutils)

later

---

### Post by chadskinner on 2004-11-06
Okay, I tried burning the CD booted to SuSE, I used CDRECORD and set the speed at 0x (BTW - I also used the KDE CD Burner and it decided on 0X after checking the ISO and the drive).  Both times I get the same BSDUTILS eroor.

What's more interesting is that it tells me the CD Image will be only 302MB?  I thought it was 550 or something.

Either way I'm begining to believe there is something wrong with the iso image, I'm sure it's complete but the way it was created must have a problem that some drives or utilities can't read correctly.

I'll try it on a system with a more serious CD Burner and software to see if I get any different results.

Ubuntu Folks - I know you don't feel this is your issue but I would appreciate you looking into your iso creation process or publish some BKM's on how you burn your images.

---

### Post by Mighty Mik on 2004-11-07
The windows work around is to burn it as 'raw-dao' in something like Alcohol 120%. I have to agree with this statement as well...

"Ubuntu Folks - I know you don't feel this is your issue but I would appreciate you looking into your iso creation process or publish some BKM's on how you burn your images."

end users need to be able to click on the image and burn it just as they do with any other image.

---

### Post by deech on 2004-11-10
I also burned an image under Fedora 2, using the nautilus burner.....same problem, no bsdutils....frustrating, since i really want to try ubuntu on my new laptop!!!

So what do we do now??

greetings from a rainy holland...
deech

---

### Post by deech on 2004-11-12
hmmm seems like I'm 'doomed' to install FC3!! 
Me sad...cause I wanted to try this new ubuntu so badly....

greetz,

deech

---

### Post by viniosity on 2004-12-02
Same problem here.. burned it on OSX at the lowest setting and I get the same error.  Sarge installs fine and since this installer is based on sarge I would think it would work.  This has caused me so much grief..

I'm thinking of installing Progeny or Mepis instead.

---

### Post by magillo on 2004-12-03
I had same prob, on #ubuntu irc channel GodD0t kindly suggested me to check the .iso md5sum... it didn't match!
Perhaps this is not your problem, but give it a look.
bye all

mag.

---

### Post by Arktis on 2005-02-05
> The windows work around is to burn it as 'raw-dao' in something like Alcohol 120%.
  
Just wanted to say that worked for me. I had the same error, came here, saw that, tried it and that resolved it.  Just FYI for anyone else with this issue.

---

### Post by loanmoney on 2005-02-05
All of the previous posts appear to address downloading the iso and creating a CD.  I waited and received the ubuntu CD distribution, but I am getting the same error.  I have tried 2 different CDs and they both hang at the same spot.  This seems to be more than just a bad file copy.

---

### Post by loanmoney on 2005-02-05
OK, I've been playing with this install all afternoon.  My wife is NOT happy that I wasted a Saturday!  I finally brought in a 2nd system.  The ubuntu distro is ver 4.10.  I was originally attempting to install on an old HP Vectra.  After trying several configuration variants, including a different HD, I finally started the install on an old Compaq Deskpro.  It got past the bsdutils and moved right thru the install!  Now I have to take back some of the nasty things I've said about Compaq!  I worked at DEC when Compaq bought them and destroyed all things DIGITAL.  But I digress!

The moral here is that the bsdutils problem you are having may not be a bad distrubution.  Maybe your hardware just isn't ready for LINUX.

I am trying to set this system up as a network print server.  I'll reserve complete judgement of ubuntu until I am able to locate drivers for all the printers (and the extra parallel i/o cards).

---

### Post by jcredberry on 2005-02-06
I believe it is a little of both, hardaware and distribution problems. I'm using VMWare and I used two original distribution CD's and one image burned CD to no avail. Then I used the image as the CD source and it passed the bsdutil problems but got stucked while copying files to the /target directory. Think I'm getting a little pissed about this and I'm not going to continue suffering. Think I'm going to download Fedora!!!  Great way to go Ubuntu team!!! =D>

---

