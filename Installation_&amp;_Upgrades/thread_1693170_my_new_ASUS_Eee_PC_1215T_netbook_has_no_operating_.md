---
title: "my new ASUS Eee PC 1215T netbook has no operating system"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by agnisflugen on 2011-02-22
[SIZE=4]**i ordered an AsuS **Eee PC 1215T [/SIZE][SIZE=3][B][SIZE=4]netbook off of Newegg:

[http://www.newegg.com/Product/Product.aspx?isfeedbacktab=true&item=34-220-857&keywords=%28keywords%29&page=1&pagesize=10&selectedrating=-1&sortfield=0&summarytype=0&videoonlymark=False&RandomID=51941991301877020110222103150](http://www.newegg.com/Product/Product.aspx?isfeedbacktab=true&item=34-220-857&keywords=%28keywords%29&page=1&pagesize=10&selectedrating=-1&sortfield=0&summarytype=0&videoonlymark=False&RandomID=51941991301877020110222103150)

i was confused and surprised to discover it didn't have an operating system, only the Express Gate Cloud. it was advertised as running on windows 7, but it's not installed. i called the ASUS tech support not once, but TWICE and they didn't know diddly squat. would anyone be able to walk me through how to install linux on it? the express cloud is a very basis system. there isn't a "my computer" function so i don't know how i would go about installing anything on it. from what i understand this little netbook has great potential, i just don't know how to harness it. any advise would be greatly appreciated! linux is new and confusing to me, but i hope to someday become proficient in it.[/SIZE]
[/B][/SIZE]

---

### Post by zvacet on 2011-02-22
Download Maverick from [here]("http://releases.ubuntu.com/maverick/") and read [this]("https://help.ubuntu.com/community/GraphicalInstall") about installing.I think you will choose side by side,because you already have one OS installed.

---

### Post by agnisflugen on 2011-02-23
well i'm a little closer to figuring out...i followed the steps as detailed on the ubuntu website:

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

i downloaded the netbook version, downloaded the universal USB installer, installed it on my USB, and then i stuck it in my new netbook, and then i got stuck. i didn't know what buttons to push during the set up process, so then i found this video:

[http://www.youtube.com/watch?v=xEUlczV2ggI](http://www.youtube.com/watch?v=xEUlczV2ggI).

whick walked thru the steps, push F2 during start up, disable boot booster, select 2nd boot devise, hit pf 10, restart, hit ESC and then the Ubuntu set up screen came up. i was excited! i went all the way to almost the very end of set up, when DRATS!  i received the following dreaded error message: 

 "(Errno 5) Input/output error

this is often due to a faulty CD/DVD disk or drive or a faulty hard disk. it may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD lens, to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment."
  
i don't understand?!? i'm not using a CD but rather a USB, and how can the hard disk be old or junky if the laptop is new out of the box? 

anyone else encounter this error during set up, and if so what did you have to do to get passed it?

---

### Post by Quackers on 2011-02-24
Check the md5sum of the downloaded iso file 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok, when next booting from the usb, on the first purple screen (with the little man icon at the bottom) press Esc then choose your language. On the next screen choose the option to check the cd for errors (it doesn't matter that you are using a usb key rather than a cd - the check is the same).
One arror on the usb is too many. The iso file needs burning again.

---

### Post by agnisflugen on 2011-03-01
thank you! i was able to get the netbook version successfully loaded last nite....i had to delete all the files, reload them, and try again. not sure what went wrong the first time, but it's working now :)

---

### Post by Quackers on 2011-03-01
Nice one :-) Sometimes it's a bad burn or a bad read. It is usually best to select a slow burn speed as it can eliminate errors.
Enjoy!

---

