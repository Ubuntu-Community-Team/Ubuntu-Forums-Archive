---
title: "How to get hold of Opera 11.61 within Ubuntu 10.10?"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2012-03-25
Hello There!

I have just updated my Ubuntu 10.10 with upgrades of worth 228MB in size. Alas, Browser Opera still remain stuck with 11.52 only, whereas it should have been migrated to 11.61.

Browser's Help>>Check for Updates yield an Outcome that suggests to make this transition using an your OS inbuilt upgrade mechanism only.

Could anyone please help me steer through to get hold of latest 11.61 version of Opera in a relatively easiest of ways?!

Help will be sincerely appreciated.

---

### Post by PaulW2U on 2012-03-25
You can always get the latest stable release from [http://www.opera.com/download/](http://www.opera.com/download/).

---

### Post by whatthefunk on 2012-03-25
If you add the Opera ppa you should be able to upgrade normally.

[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by Saurabhdua on 2012-03-25
Oh My God!

Wish if this platform had provided a 'Remote Assistance' facility to enable wise Guys like your goodself to remotely control my machine & help run those 'Wild n Whacky' commands of Linux!

Mere a glimpse of that page brought back the reminisce of Mr. Bean's episode @ Laundry, increasingly getting hesitant n bullied by a Street Guy :-)

---

### Post by stinkeye on 2012-03-25
Check in Software sources that the opera ppa is enabled or existing.
When you  first download and install opera from [**_[COLOR="DarkRed"]http://www.opera.com/download/[/COLOR]_**]("http://www.opera.com/download/")
the ppa is added automatically.
May have been disabled in the upgrade.

---

### Post by TejasMChavan on 2012-03-25
sudo dpkg -i /home/<your user name>/Downloads/opera_11.61.1250_i386.deb

Download .deb file from opera.com.

Assuming the .deb file is downloaded in Downloads folder put command above in terminal. Be careful about capital and small letters in path.
If your unsure about the path right click on .deb file you have downloaded and properties. You'll see file path.
Also replace "opera_11.61.1250_i386.deb" with filename of .deb you have downloaded from opera.com

---

### Post by Saurabhdua on 2012-03-26
Hello Stinkeye!

I did check the very screen. Though, Final or Stable release goes "Check Marked", I did try out the enabling the Opera's Pre-release option.

Window did show up with 11.61 as an update but couldn't install the same since installation pre-maturely ended up with an error message quoting::"Requires installation of untrusted packages"!!?

Any ideas to remedy?

---

### Post by Hakunka-Matata on 2012-03-26
Software sources: enable restricted


good luck

---

### Post by whatthefunk on 2012-03-26
> **Hakunka-Matata said:**
> Software sources: enable restricted


good luck

Enable restricted has nothing to do with Opera...its for proprietary drivers for devices.  He needs to add and enable the Opera ppa under the Other Software tab.

---

### Post by stinkeye on 2012-03-26
If you have the opera repository enabled (pic1)
check you have the signing key (pic2).
If not add the signing key in the terminal (copy and paste including the trailing "-" )
```
wget -qO - http://deb.opera.com/archive.key | sudo apt-key add -
```


Then run 
```
sudo apt-get update
```

Open update manager and check for an update to Opera.


If that doesn't work, just download and install the latest deb
from [**_[COLOR="DarkRed"]http://www.opera.com/browser/download/[/COLOR]_**]("http://www.opera.com/browser/download/")

---

### Post by Saurabhdua on 2012-03-27
Thanks to all of you!

I have been able to upgrade my Opera to 11.61 through Ubuntu Software Center.Thankfully, Opera's installation did came pack with well recognized .deb package.

---

### Post by PaulW2U on 2012-03-27
Opera 11.62 was released this morning so you should be getting notified of a further update very soon. :p

---

### Post by Saurabhdua on 2012-03-28
Yes indeed! I did update my Opera to 11.62 yesterday only!..& this time there were no frills or intimidation(remember Mr. Bean!?) :-)

---

