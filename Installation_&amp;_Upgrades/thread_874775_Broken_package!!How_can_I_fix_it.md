---
title: "Broken package!!How can I fix it?"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by ultimate_aektzis on 2008-07-30
As told in the title...I just installed ubuntu one more time but system says that there are broken packages.More speciffically
says that 
> You have 1 broken package on your system!

Use the "Broken" filter to locate it.

Any help on that.
thanks in advance:)

---

### Post by Partyboi2 on 2008-07-30
Open a terminal (Applications>Accessories>Terminal) and type
```
sudo apt-get -f install
``` or open up Synaptic Package Mananger (System>Admin>Synaptic Package Mananger) and go to Edit>Fix broken package

---

### Post by iaculallad on 2008-07-30
System->Administration->Synaptics Package Manager, click on Edit->Fix Broken Packages.

---

### Post by ultimate_aektzis on 2008-07-30
Hmm,nothing special happened.Neither from terminal nor from synaptic.
After terminal failed I saw this message(Attachment)

---

### Post by Geeke on 2008-07-31
is that Russian? If so try downloading this package and seeing if it will work. 

[http://packages.ubuntu.com/dapper/all/language-support-ru/download](http://packages.ubuntu.com/dapper/all/language-support-ru/download)

---

### Post by zvacet on 2008-07-31
It is Greek and you can try to download and install package from [here.]("http://packages.ubuntu.com/search?keywords=language-pack-el-base&searchon=names&suite=hardy&section=all")

---

### Post by darkwing-abandoned on 2008-08-02
Hi. I am new to this and I'm hoping someone can help me. When I click on the update manager, is gives a message: 

Software index is broken. It is impossible to install or remove any software. Pls use the package manager“Synaptic”or run “sudo apt-get install -f”in a terminal to fix this issue at first.

I then open Synaptic and 3 packages, mysql-admin, my-sql-navigator and mysql-query-browser come up as the broken dependancies. I then click Edit>Fix broken packages and nothing happens. I then click apply and the summary window appears. I click apply again and the window “Please insert the disk labeled:
main-restricted
in drive /cdrom/” appears. I insert the disk and click ok. The window flickers and does not disappear no matter how many times you click ok. It does not start downloading the packages. Instead, the DVD recorder browser window appears. I navigate down to /pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.24a-9_all.deb. I double click that file to install it and get the broken dependancies message again. 

I tries the “sudo apt-get install -f”command from the terminal but that tells me I don't have the necessary permissions. 

PLEASE can someone tell me how to stop going round in circles!!!! 

Thanks

---

### Post by oldos2er on 2008-08-02
"I tries the &#8220;sudo apt-get install -f&#8221;command from the terminal but that tells me I don't have the necessary permissions." Are you certain you typed "sudo" in front of that command? Did the system ask you for your password?

---

### Post by darkwing-abandoned on 2008-08-02
Hi. Yes, the system asked me for my password. But first, it identified the dependancies that needed to be corrected and asked if I wanted to continue. I Typed y and hit enter. It then asked me to insert the appropriate disk and hit enter, which I did. Nothing happened except that the file browser for the DVD popped up.

---

### Post by Kevbert on 2008-08-02
It may be worth removing/purging the faulty packages in terminal with:
```
sudo apt-get remove --purge *packagename*
```  where *packagename* is the name of each of the packages that you wish to remove.  [COLOR="Red"]Be careful that you to not make any mistakes with this command as it could make your system unusable.[/COLOR]
If you want to you can re-install them as normal afterwards. It also looks like you have the CD ticked in Software Sources (under the Ubuntu Software).  It may be worth removing the tick to stop the CD being prompted for.

---

### Post by darkwing-abandoned on 2008-08-02
I'm a bit worried about removing packages entirely since these seem pretty important (mysql-admin, my-sql-navigator and mysql-query-browser). I would hate for the system to become unusable....

---

### Post by Partyboi2 on 2008-08-03
Have you unticked the cd rom box in Software Sources? Go to Software Sources (System>Admin>Software Sources) and on the first tab untick the cd rom box then close Software Sources then open up a terminal (Applications>Accessories>Terminal) and type
```
sudo apt-get -f install
```

---

### Post by ultimate_aektzis on 2008-08-03
Ok I managed to solve the problem.What did I do?.when I tried to update my system it prompted me to make a partial update and so I did.After restarting the computer everything was ok.Anyway things are ok so I would I like to thank you for your time=D>):P

---

### Post by darkwing-abandoned on 2008-08-04
-

---

### Post by darkwing-abandoned on 2008-08-04
I did as you said Kevbert and Partiboi2 - unchecked the boxes in software sources and typed in the command in the terminal window but alas....the same thing happened. I am beginning to wonder if I shouldn't just get a copy of 8.04 (this version is 6.10) and just do a fresh install - that should sort it out???

Thank you both for you advice.

---

