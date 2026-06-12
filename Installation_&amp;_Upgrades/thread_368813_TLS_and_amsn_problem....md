---
title: "TLS and amsn problem..."
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by EngineerJoe on 2007-02-23
I recently installed Ubuntu 6.06 and since, I have compiled and installed amsn (apt get did nothing), and when I try to log on amsn, I am prompted with the TLS module install wizard. I select my version of Linux and click "ok". I am then told that the TLS module installation was successful and I should be able to use MSNP9. Then it goes right back to amsn unchanged (it doesn't even try to login). If I click "login" again, I am prompted with the same TLS mod install wizard. I know an infinite loop when I see one and I'm wondering what is wrong?

Also, I know I shouldn't be picky when asking for help, but please remember the following
1. I've used amsn and gaim. I don't like gaim. Please do not suggest I use gaim as my fix to amsn not working, because using that logic, I should use windows because my ubuntu isn't working perfectly

2. Please do not tell me I should have searched for this solution. I did. I found nothing which is obviously why I'm here with this post.

---

### Post by NosLycn on 2007-02-24
Try > sudo apt-get install tcltls

That should install tcl/tls and get rid of that monkey from your back.  See if it still asks you to install.

I am surprised that apt-get found nothing for amsn.

Try the following repository (may be slow, depending on your location):

> deb [http://debian.yorku.ca/ubuntu/](http://debian.yorku.ca/ubuntu/) dapper main restricted universe multiverse

apt-get update and apt-get install amsn

Please note that it will not install the newest amsn (at least it never has for me).  For that, you would need to get the autopackage package from the amsn website, but you probably know that already.

Good Luck

~Dave

PS.  I understand when you say you don't want to use gaim for msn.  I understand in full.

---

### Post by Glennji on 2007-02-26
I had the same problem, installed tcltls but no luck.  Then I found a "make AMSN anti-aliased" script and had a wee look -- one of the steps was to edit the file:

```
/usr/lib/tls-1.50/pkgIndex.tcl
```and append a 0 to the end of the first version reference i.e. the line now looks like:

```
package ifneeded tls 1.50 "[list load [file join $dir .. libtls1.50.so] ] ;[list source [file join $dir tls.tcl] ]"
```

Worked!  Try?

---

### Post by rictus007 on 2007-03-22
Ok this is what I do...
1) sudo apt-get install tcltls
2) I went to aMSN and once again apear the screen to download the proper TLS - I selected the correct one and this time ...AMSN works


By the way...I also don't like gaim

---

### Post by faminator on 2007-05-16
> **Glennji said:**
> I had the same problem, installed tcltls but no luck.  Then I found a "make AMSN anti-aliased" script and had a wee look -- one of the steps was to edit the file:

```
/usr/lib/tls-1.50/pkgIndex.tcl
```and append a 0 to the end of the first version reference i.e. the line now looks like:

```
package ifneeded tls 1.50 "[list load [file join $dir .. libtls1.50.so] ] ;[list source [file join $dir tls.tcl] ]"
```

Worked!  Try?

Thanks.
This helped me.

---

### Post by Nameless One on 2007-05-17
If the above information doesn't work, you can try this.
I had the same problem and had tried everyones advice with no tangible result. It took me some time to figure it out, but this worked for me.
After you have been through the process of installing the TLS module and made sure the 'pkgindex.tcl' file has the line
```
package ifneeded tls 1.50 "[list load [file join $dir .. libtls1.50.so] ] ; [list source [file join $dir tls.tcl] ]"
```
you should then make a symbolic link between the '/usr/lib/tls1.50/' folder and your '~/.amsn/plugins/' folder:
```
sudo ln -s /usr/lib/tls1.50/ ~/.amsn/plugins/
```
Once back in aMSN, it should log in fine.

---

### Post by quinnten83 on 2007-05-20
HI I've done all that has been suggested in this thread, but i'm still having problems with the update of amsn in feisty.
I've downloaded the files myself, made a link and still nothing.
Also I can't append the "0" in the original tlc link, because the folder is read only.
do you guys have any other suggestion?

---

### Post by hakan69 on 2007-05-20
Hi!
Try this: Open a terminal window, type "sudo gedit /usr/lib/tls1.50/pkgIndex.tcl" (or where ever your pkgindex-file is)
Now you should be able to save your changes.

Regards Hakan

---

### Post by patrickfromspain on 2007-05-22
if you have troubles with tls, try using this one I attach. Please say if it works.

---

### Post by edu barros on 2007-05-22
> **Nameless One said:**
> If the above information doesn't work, you can try this.
I had the same problem and had tried everyones advice with no tangible result. It took me some time to figure it out, but this worked for me.
After you have been through the process of installing the TLS module and made sure the 'pkgindex.tcl' file has the line
```
package ifneeded tls 1.50 "[list load [file join $dir .. libtls1.50.so] ] ; [list source [file join $dir tls.tcl] ]"
```
you should then make a symbolic link between the '/usr/lib/tls1.50/' folder and your '~/.amsn/plugins/' folder:
```
sudo ln -s /usr/lib/tls1.50/ ~/.amsn/plugins/
```
Once back in aMSN, it should log in fine.

that worked.
thanx! :D

---

### Post by tugh on 2007-05-26
It worked for me!! Thanks...:D

---

### Post by quinnten83 on 2007-06-06
It worked for me too.
reinstalling the tls packages and appending the 0 trick.

---

### Post by kschelde on 2007-06-07
> ```
package ifneeded tls 1.50 "[list load [file join $dir .. libtls1.50.so] ] ; [list source [file join $dir tls.tcl] ]"
```
you should then make a symbolic link between the '/usr/lib/tls1.50/' folder and your '~/.amsn/plugins/' folder:
```
sudo ln -s /usr/lib/tls1.50/ ~/.amsn/plugins/
```
Once back in aMSN, it should log in fine.

I tried all of this in this page but my amsn still don't work. I'm a feisty fawn user.

---

### Post by reisyboy on 2007-06-07
try opening a terminal and typing

```

sudo apt-get install tcltls

```

---

### Post by Nameless One on 2007-06-10
> If the above information doesn't work, you can try this.
 I had the same problem and had tried everyones advice with no tangible result. It took me some time to figure it out, but this worked for me.
 After you have been through the process of installing the TLS module and made sure the 'pkgindex.tcl' file has the line
 
```
package ifneeded tls 1.50 "[list load [file join $dir .. libtls1.50.so] ] ;[list source [file join $dir tls.tcl] ]"
```
you should then make a symbolic link between the '/usr/lib/tls1.50/' folder and your '~/.amsn/plugins/' folder:
 
```
sudo ln -s /usr/lib/tls1.50/ ~/.amsn/plugins/
```
Once back in aMSN, it should log in fine.
This is it:
1.) Go to your '/home/"USERNAME HERE"/.amsn/plugins/' folder and delete the folder 'tls1.50'.
2.) Go to your '/usr/lib/' folder and delete the folder 'tls1.50'. (You will need to be in a file manager with root permissions, just type in a console 'sudo nautilus or sudo thunar or sudo konqueror').
3.) With all traces of the old 'tls1.50' gone, now type in a console
```
sudo apt-get install tcltls
```
4.) Now we need to edit the 'pkgIndex.tcl' file in the new 'tls1.50' folder. Type into a console
```
sudo gedit '/usr/lib/tls1.50/pkgIndex.tcl'
```
Replace 'gedit' with your text editor of choice, such as 'kedit' or 'mousepad'
5.) Once the file is open change the line
```
package ifneeded tls 1.5 "[list load [file join $dir .. libtls1.50.so] ] ; [list source [file join $dir tls.tcl] ]"
```
to
```
package ifneeded tls 1.50 "[list load [file join $dir .. libtls1.50.so] ] ; [list source [file join $dir tls.tcl] ]"
```
by appending a 0 to the end of 'tls 1.5'.
6.) Save and close the file.
7.) NOW enter this into a console, substituting "USERNAME HERE" for the name of the user you are on at the time
```
sudo ln -s /usr/lib/tls1.50/ /home/"USERNAME HERE"/.amsn/plugins/
```
8.) It should work now.

---

### Post by kr0n1x on 2007-12-12
i needed only the symbolic link, thanks:)

---

