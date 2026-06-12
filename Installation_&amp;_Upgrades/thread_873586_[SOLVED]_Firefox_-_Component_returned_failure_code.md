---
title: "[SOLVED] Firefox - Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) ..."
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by awam66 on 2008-07-29
Firefox - Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIStringBundle.formatStringFromName]

I am having a problem with Firefox on my Hardy installation after an update the other day. When I run Firefox 3 I get the above error and the result is none of the bookmarks work and the forward and back keys are greyed out, the history is blank also. I have looked at a bug report with the same error but it is incomplete and expired.
My system is AMD 64 Architecture. Looking in the .mozilla folder in my home folder the firefox-3.0 folder has been changed to forefox-3.0.abandoned. Tried changing it back without the abandoned but got same message and the folder has again been changed as above. Any ideas please?

---

### Post by Kevbert on 2008-07-29
If the firefox package is broken you could try
```
sudo apt-get install -f
```
from the terminal command line.  Then try updating
```
sudo apt-get update
```
If you try the update command first you may find that a broken package error occurs.  Otherwise it looks like a re-install is in order.

---

### Post by awam66 on 2008-07-29
Thanks, tried these comands nothing required. I have also de-installed and re-installed Firefox 3. No change:lolflag:

---

### Post by awam66 on 2008-07-29
Well I decided to completely remove all applications relating to Firefox and re- installing only firefox three, no gnome support etc. It is now working. All a bit of a mystery though.

---

### Post by Kevbert on 2008-07-29
Did you just perform a removal or did you purge all ?

---

### Post by awam66 on 2008-07-29
I just did a removal

---

### Post by Kevbert on 2008-07-29
For problems like that it's probably better to purge the package with
```
sudo apt-get remove --purge *filename*
```
[COLOR="Red"]The only problem with this command is that if you get the command wrong you could do untold damage to the file system[/COLOR].

---

### Post by awam66 on 2008-07-29
> **Kevbert said:**
> For problems like that it's probably better to purge the package with
```
sudo apt-get remove --purge *filename*
```
[COLOR="Red"]The only problem with this command is that if you get the command wrong you could do untold damage to the file system[/COLOR].

Yes thanks for that.
As I say I did a normal remove and reinstall and it worked. Odd it didn't do that the first time I tried.

---

### Post by genericcitizen on 2008-08-03
Hi,

Just for those who are still experiencing the error,

For me it seems it was related to the Forecastfox add-on, as I was still getting the error after a reinstall of FF and only removing Forecastfox fixed it.  

For those still seeing that annoying component failure code worth a try.

---

### Post by Thaddeus11 on 2008-08-06
Hi all,

I encountered the above error this morning after booting up my PC but found my problem/resolution was different so I figured I'd share in case the above doesn't help resolve for some people.

I checked my ./mozilla directory and found that there were files in there with root:root permissions and that my username did not have permissions to read/write.

This may be overkill but I chown'd everything under ./mozilla and it resolved my problem.

Open a terminal window and run the following:

```
cd ~/.mozilla
chown -R *username:username* *
```

where *username* is your login name.

The cd ~/.mozilla moves you to the .mozilla directory under your home directory.
The chown command sets ownership of the files.
The -R flag is recursive which means it will not only look at files/folders in the current directory but also go into subdirectories.
The * (asterisk) means all files/folders.

Hope this helps.

---

### Post by loolee on 2008-08-14
I've still the same problem...:(

---

### Post by billybag on 2008-08-17
```
sudo chown -R myname:mygroup ~/.mozilla
``` where as myname and mygroup is your username that you loigin with.

---

### Post by Barney on 2008-09-08
BIG THANKS! ...worked for me.

Error originally occurred after sudo-ing Firefox for something,

---

### Post by dalee on 2009-01-21
> **Thaddeus11 said:**
> Hi all,

I encountered the above error this morning after booting up my PC but found my problem/resolution was different so I figured I'd share in case the above doesn't help resolve for some people.

I checked my ./mozilla directory and found that there were files in there with root:root permissions and that my username did not have permissions to read/write.

This may be overkill but I chown'd everything under ./mozilla and it resolved my problem.

Open a terminal window and run the following:

```
cd ~/.mozilla
chown -R *username:username* *
```

where *username* is your login name.

The cd ~/.mozilla moves you to the .mozilla directory under your home directory.
The chown command sets ownership of the files.
The -R flag is recursive which means it will not only look at files/folders in the current directory but also go into subdirectories.
The * (asterisk) means all files/folders.

Hope this helps.

Hi,

Thanks! I just ran into this problem. Changing the permissions back worked. I had just installed Google Earth and ran it as Sudo by accident. I was searching for directions and it called up Mozilla to print. I suspect that is where my problem originated.

Again, Thank You!

dalee

---

### Post by PaulW on 2009-02-24
Thanks, Thaddeus11.  Your chown suggestion worked for me!:)

---

### Post by at78rpm on 2009-06-01
Whoa, THANK YOU!  Thaddeus11, you saved my day.  What I most appreciate is that you not only provided the terminal commands, but you also explained what each one does.  My Firefox is back to normal, thanks to you.

---

### Post by cocolocko on 2009-06-13
```
sudo chown -R myname:mygroup ~/.mozilla
```

I had the problem with the Addon "Forecastfox" and i solved it with the command succesful!

Thanks

Greetings

---

### Post by digitalghost1 on 2009-08-02
Thank you very much for the commands I was going insane trying to correct this problem. :mrgreen::mrgreen::mrgreen::cool::cool: 

ubuntu forums to the rescue!

---

### Post by olvlo on 2009-09-14
Worked like a charm. Thanks a lot!

---

### Post by Landie_UK on 2009-11-14
Hi I tried the following
> cd ~/.mozilla
chown -R username:username *

I got "operation not permitted" after every time it tried to change the file permissions. I did this and it worked

code>  sudo chown -R username:username *

hope this helps

---

### Post by azteech on 2009-12-05
Hi,

Just thought I would let you all know that this problem is still around. 

However, my problem occurred after going into Firefox safe mode and removing Torbutton 1.2.0 (which can only be uninstalled in Firefox safe mode). After rebooting and re-starting Firefox, I received the following error - **NS COMPONET FALIURE: Component returned failure code: 0x80004005 (NS_ERROR_FAILURE)**. 

After googling the web, found this link. Noticed that Forecastfox was mentioned as possible issue. Uninstalled the Forecastfox extension, restarted Firefox, and the error vanished.

For those still seeing that annoying component failure code it may be worth a try removing Forecastfox extension (if you have it installed). If it clears up the error you can 1) either leave it removed, or 2) re-install it and reboot Firefox for it to take effect.

If you are seeing the above error, AND you do not have the Forecastfox extension installed, then try removing each Firefox extension, one at a time, until you find the offending extension. Remove the extension and restart Firefox. If you need (or wish to continue to use) the extension you just removed, then all you have to do is re-install it and restart Firefox once more for the extension to be activated.

p.s. - Still not sure why removing the Torbutton 1.2.0 extension would affect the Forecastfox extension, but it did. But that is something that the dev's and mozilla team should investigate.

---

### Post by jwatne on 2010-01-16
Add my voice to the choir of those thanking you for this solution!

> **Thaddeus11 said:**
> Hi all,

I encountered the above error this morning after booting up my PC but found my problem/resolution was different so I figured I'd share in case the above doesn't help resolve for some people.

I checked my ./mozilla directory and found that there were files in there with root:root permissions and that my username did not have permissions to read/write.

This may be overkill but I chown'd everything under ./mozilla and it resolved my problem.

Open a terminal window and run the following:

```
cd ~/.mozilla
chown -R *username:username* *
```

where *username* is your login name.

The cd ~/.mozilla moves you to the .mozilla directory under your home directory.
The chown command sets ownership of the files.
The -R flag is recursive which means it will not only look at files/folders in the current directory but also go into subdirectories.
The * (asterisk) means all files/folders.

Hope this helps.

---

### Post by ramonimo on 2010-04-02
I have solved the problem doing the prior indicated:

cd ~/.mozilla
chown -R username:username *

How did i have such a problem?
I was doing the fool and i executed firefox from console: sudo firefox.

After that when i launched firefox the normal way, suddenly the "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) ..." appeared

---

### Post by kilroy0097 on 2010-04-10
I have also solved the problem doing the prior indicated:

cd ~/.mozilla
chown -R username:username *

Except I actually had to su as root in order to do this.

I was trying to think of how this happened. Then I realized that I attempted to unpackage and install a different version of firefox but realized it was not for 64 bit architecture. I did so as sudo as well.

So probably the combo of those two things messed it up. Why? I have no idea.

After that when I attempted to start up firefox I got the "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) ..." error.

Removing FoxCast that weather AddOn actually removed the error but did not fix the behavior of Firefox. I had no bookmarks, no forward or back browser buttons. It would not load into my Homepage and many pages it would never stop loading the page. All in all very possessed Firefox.

---

### Post by pibach on 2010-06-22
> **genericcitizen said:**
> Hi,

Just for those who are still experiencing the error,

For me it seems it was related to the Forecastfox add-on, as I was still getting the error after a reinstall of FF and only removing Forecastfox fixed it.  

For those still seeing that annoying component failure code worth a try.

De-installation of ForecastFox did it for me as well, thanks for that hint.

---

