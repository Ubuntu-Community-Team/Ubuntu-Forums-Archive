---
title: "How can I install Geogebra in Ubuntu 20.04 ? (hint not possible through repository)"
date: 2021-02-21
forum: Installation &amp; Upgrades
---

### Post by elpidiovaldez5 on 2021-02-21
The version of Geogebra in the repository is 4.0.34.0+dfsg1-7, and it hangs as soon as it starts.

Mr Google recommends installing Geogebra Classic 5 or 6 from the  [geogebra.org]("https://wiki.geogebra.org/en/Reference:GeoGebra_Installation#GeoGebra_Classic_6") website, however the links to the 64 bit version for linux are broken....

There is some mumbo jumbo about adding the geogebra repository.  I followed the instructions, but there is a problem with a gpg key and I have no idea how to fix that.

Geogebra is a very useful tool which I have used many times in the past.  It seems a shame that it is so hard to install, and that the bugs are so evident, but remain unfixed.  The alternative, KSEG ceased to be maintained years ago.

---

### Post by howefield on 2021-02-21
> **elpidiovaldez5 said:**
> ... I followed the instructions, but there is a problem with a gpg key and I have no idea how to fix that.

The key is linked to from the applications website.

Download it and use the Software & Updates application to add it to your system. Software & Updates > Authenticaion tab > Import New Key...

Haven't tried installing the application but if it doesn't work it shouldn't be for the lack of adding the key.

---

### Post by elpidiovaldez5 on 2021-02-21
> **howefield said:**
> The key is linked to from the applications website.

Download it and use the Software & Updates application to add it to your system. Software & Updates > Authenticaion tab > Import New Key...

Haven't tried installing the application but if it doesn't work it shouldn't be for the lack of adding the key.

Thank you for your help.  I did not know about the authentication tab on software updates.  I had already downloaded the key, but did not know how to use it.  Actually, I still don't, because the 'Import Key File' button at the bottom of the authentication tab does nothing when I press it.  I presume I am meant to see a file dialog that lets me browse to the key file.

Google found the  [manual]("https://manual.lubuntu.me/stable/4/4.3/software_sources.html").  It explains everything beautifully, except how to use the 'Import Key File' button !

So now I need to know if this functionality never works, or if there is something specific to my system that is stopping me using it.

---

### Post by elpidiovaldez5 on 2021-02-21
I have finally cracked it (after a few hours).  To install Geogebra Classic 6 (which actually seems to work !), do the following:

> wget -q -O - [http://www.geogebra.net/linux/office@geogebra.org.gpg.key](http://www.geogebra.net/linux/office@geogebra.org.gpg.key) | sudo apt-key add -
sudo apt-add-repository -u 'deb [http://www.geogebra.net/linux/](http://www.geogebra.net/linux/) stable main' 
sudo apt install geogebra-classic


The first line is the vital step.  It would be nice if the developer's of Geogebra would fix their broken links, and add this snippet of information for simple users who do not understand the guts of linux' security system.

[Warning] You can't copy and paste the code that I provided.  Despite enclosing it in quotes, the editor insists on changing the urls, by adding ellipsis (which is what you get when you copy and paste).  I am tired of struggling with it.  Modern software is too complicated, which is why nothing ever works properly !

Still lots of thanks to @howefield, for pointing me in the right direction.

---

### Post by howefield on 2021-02-21
Glad you got it sorted, the next step was to point you to the command line method to add the key.

As an aside, tried importing the key into a 20.04.2 with the Software & Updates application and it worked perfectly fine, but don't have any ideas as to why it failed for you.

---

### Post by elpidiovaldez5 on 2021-02-21
I just tried to use the 'Import Key File' button again.  Same result .... nothing.  Software sources dialog asks me to supply admin password when I open it, which I do. This will have to wait for another day.  I am exhausted from my battle to install Geogebra.  Thanks for your help though.

---

### Post by Hagar Delest on 2021-02-21
Why don't you just install from the deb downloaded from the website? I just tried and the link is fine (64bit .deb version).
Then "sudo dpkg -i *.deb" in a terminal in the folder where you've downloaded the file (make sure there is no other .deb there).
I used to install it like that in the past and it works fine.

---

