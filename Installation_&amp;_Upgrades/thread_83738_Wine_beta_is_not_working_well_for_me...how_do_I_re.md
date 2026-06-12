---
title: "Wine beta is not working well for me...how do I revert?"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by dougr on 2005-10-29
I am trying to install DVD decrypter and DVD shrink, and I am having a problem with no devices being found, etc.  It seems like a lot of problems people are having are due to the new version of wine which I upgraded to.  I want to revert to an old version,, but cannot find any sources.  Any ideas?

---

### Post by claydoh on 2005-10-29
Try running winecfg in a terminal window, go to the Drives tab and then try the Autodetect button. A default wine setup only detected my root directory and the "fake" c-drive. After running that, it detected all my partitions, my 2 optical drives, and even my usb pen drive.

---

### Post by dougr on 2005-10-29
wine works fine...the problem is this new version of wine and dvd decrypter

---

### Post by claydoh on 2005-10-29
I successfully installed both and am working on a quick how-to :)

---

### Post by claydoh on 2005-10-29
[From this guide as a basis]("http://www.mrbass.org/linux/ubuntu/dvdshrink/"), I installed both DVD Decrypter and dvd shrink using wine .9 beta in Kubuntu Breezy

([COLOR=#000000]S[/COLOR]kip installing winesetuptk as mentioned in the guide)
First, place a dvd in your drive.
Then start with a clean wine install, removing your original ~/.wine directory.
(this may not be necessary, but I am unsure if upgrading an existing wine setup from the old version will work)

Open a terminal window and type the following command:
```
$ winecfg
``` 
This sets up a basic wine config, and opens a nice config program;
In the "drives" tab, click on "add" then "browse", and navigate to your dvd drive. Make sure the folder you select is not a link to another folder in /media, such as /media/cdrom, which for me points to /media/cdrom0. I selected cdrom0 then hit the "Advanced" button, selected "cdrom" in the "type:" drop-down box, and clicked "Apply". This sets up a "d:" that points to my DVD drive.
If you wish, you can then use the "Autodetect" button to make all your other mounted partitions visible to wine, which is usefull if you want to run a setup program that may be on another drive.

Next, run the SetupDVDDecrypter_3.5.4.0.exe and installed the program using all the default options. It will run after the install, with an error about no devices found, so close the program (from the File menu - I find that sometimes just closing the program window in wine may not shut down wine completely) and go back to winecfg, this time going to the "Applications" tab. Click the "add application" button, and browse to /program files/DVD decryptor/DVDDecrypter.exe" and set the Windows version to "Windows NT 4.0" . Click "apply" once more. Then navigate to the exe file located in ~/.wine/drive_c/Program Files/DVD Decrypter/and double-click DVDDecrypter.exe. (In Kubuntu Wine puts a desktop link to the program on my KDE desktop. I am unsure if it will do so in Gnome.)

Now for DVD Shrink, just follow the steps in the [original guide]("http://www.mrbass.org/linux/ubuntu/dvdshrink/"), starting at the step where you download the dll.zip file.

I have not actually used the programs yet, but I imagine they should work as they used to in older versions of wine.

---

### Post by dougr on 2005-10-29
That is exactly what I did.  The reason it worked for you is because you are running breezy, and I am still in hoary.  For some reason this causes a problem.  I have thought of upgrading to breezy but am worried about things breaking.

Thanks

---

### Post by claydoh on 2005-10-29
I will install Hoary and see what the difference might be

---

### Post by dougr on 2005-10-29
wow, that would be terrific.  Thanks a lot for all of your help.  Everything appears fine on my system, and it seems others have had this problem with the new version of wine and hoary.

---

### Post by claydoh on 2005-10-30
Ok I think I have it!

You will need to install libstdc++6 for wine 0.9 beta to run.

I did see my DVD disc in DVD Decrypter at one point, but that drive ( on my test box) has been on its last legs for a while now.

---

### Post by dougr on 2005-10-31
Thank You again.  I actually do have that installed but am still having the problem.  Any other ideas?

---

### Post by mfobrien on 2005-11-02
Hi folks.  I was beating my head against this one for a while, until I saw this part of claydoh's post:

> I selected cdrom0 then hit the "Advanced" button, selected "cdrom" in the "type:" drop-down box, and clicked "Apply".

For some reason winecfg was automatically detecting everything fine, except for the fact that it was showing my dvd as a hard drive instead of a cdrom.  I changed that one little thing, and everything works smoothly again!  :) 

Claydoh, you rock!  Your attention to detail saved me after spending hours doing this  ](*,) 

Seriously, thanks!

---

### Post by claydoh on 2005-11-02
Aw, shucks!
/me blushes

> Hi folks.  I was beating my head against this one for a while, until I saw this part of claydoh's post:

I had a couple of hours to kill, so I thought I'd try and save 'yall some trouble , plus I have a thick head, as the dents in my wall can attest to ;)

---

