---
title: "[SOLVED] Synaptic Not Loading Sources List"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by xcusmwah on 2007-10-21
I was attempting to add additional sources, per the URL below (first section of the page) and after doing so I must have done something incorrectly as Synaptic is now presenting an error upon load.

**URL**
[http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html](http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html)

**Error from Synaptic**
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I am very new to Ubuntu, running 7.10 so if anyone can help me remedy this I would greatly appreciate it.

---

### Post by forestpixie on 2007-10-21
can you post the output of this - you've got an error in your sources.list

```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by xcusmwah on 2007-10-21
Wow, you are really quick.  Thank you so much!  Here is the code...


~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by forestpixie on 2007-10-21
if you're output looks like this 

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Medibuntu :: Multimedia, Entertainment &amp; Distractions In Ubuntu</title>
<meta http-equiv="Content-Type" content="text/xhtml+xml; charset=utf-8" />
<link rel="stylesheet" href="medibuntu.css" type="text/css" />
</head>
<body>
<div id="header">
<h1><span class="hidden">Medibuntu<br />Multimedia, Entertainment &amp; Distractions In Ubuntu</span></h1>
</div>
<ul id="menu"><li><a href="index.php">Presentation</a></li>
<li><a href="http://help.ubuntu.com/community/Medibuntu"> Repository Howto</a></li>
<li><a href="packages.php">Packages</a></li>
<li><a href="contact.php">Contact us</a></li>
</ul>
<div id="page">
<h2>Presentation</h2>
<p>
<strong>
Medibuntu (Multimedia, Entertainment &amp; Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc).
</strong>
</p>
<p>
Medibuntu is a packaging project dedicated to distributing software that cannot be included in Ubuntu for various reasons, related to geographical variations in legislation regarding intellectual property, security and other issues:
</p>
<ul>
<li>patentability of software, algorithms, formats and other abstract creation</li>
<li>legal restrictions on freedom of speech or communication</li>
<li>restrictions on the use of certain types of technical solution, such as cryptography</li>
<li>legal restrictions on imports of software technology, requiring for example specific permissions</li>
<li>etc.</li>
</ul>
<p>
A lot of excellent <a href="http://www.fsf.org/licensing/essays/free-sw.html">free software</a> and non-free software is affected by such restriction somewhere in the world, thus preventing its inclusion into Ubuntu that, for economy and simplicity, are generally identical for all countries.
</p>
<p>
We refuse to resign ourselves to abandoning software that may be legally useful somewhere, and we have chosen to provide it with professional quality packaging, easily usable within the context of Ubuntu.<br />
This repository provides packages for Ubuntu distribution.
</p>
<p>
It is your legal responsibility to make sure that the software you are installing can be legally used in your country and for your intended purpose.
</p>
</div>
<div id="paypal"><form action="https://www.paypal.com/cgi-bin/webscr" method="post">
<p>
<input type="hidden" name="cmd" value="_xclick" />
<input type="hidden" name="business" value="maxenced@gmail.com" />
<input type="hidden" name="item_name" value="Medibuntu" />
<input type="hidden" name="no_shipping" value="0" />
<input type="hidden" name="no_note" value="1" />
<input type="hidden" name="currency_code" value="EUR" />
<input type="hidden" name="tax" value="0" />
<input type="hidden" name="bn" value="PP-DonationsBF" />
<input type="image" src="https://www.paypal.com/en_US/i/btn/x-click-but04.gif" name="submit" alt="Effectuez vos paiements via PayPal : une solution rapide, gratuite et sécurisée" />
<img alt="" src="https://www.paypal.com/en_US/i/scr/pixel.gif" width="1" height="1" />
</p>
</form>
</div>
<div id="footer">:: designed by <a href="http://www.most-enchained.com">_Enchained</a> - logo by <a href="http://www.racoon97.net">racoon97</a> - Domain by <a href="http://flosoft.biz">Flosoft</a> - Managed by <a href="http://www.dunnewind.net">Sp4rKy</a> :: </div>
<!-- phpmyvisites -->
<a href="http://www.phpmyvisites.us/" title="phpMyVisites | Open source web analytics"
onclick="window.open(this.href);return(false);"><s cript type="text/javascript">
<!--
var a_vars = Array();
var pagename='';

var phpmyvisitesSite = 2;
var phpmyvisitesURL = "http://stats.dunnewind.net/phpmyvisites.php";
//-->
</script>
<script language="javascript" src="http://stats.dunnewind.net/phpmyvisites.js" type="text/javascript"></script>
<object><noscript><p>phpMyVisites | Open source web analytics
<img src="http://stats.dunnewind.net/phpmyvisites.php" alt="Statistics" style="border:0" />
</p></noscript></object></a>
<!-- /phpmyvisites -->
</body>
</html>

```
then do this


```
sudo mv  /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bak
```
```

sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

if all is well delete the backed up file

```
sudo rm /etc/apt/sources.list.d/medibuntu.list.bak
```

---

### Post by forestpixie on 2007-10-21
I did it again - wrong command - I've changed it in the first post - do it again with revised code then my second post again :)

---

### Post by xcusmwah on 2007-10-21
Thanks for the fix, I am now able to get into Synaptic.  I could be wrong but when I go into Synaptic now it seems like an older version than the one I had.  The one I had enabled you to see votes/stars for how popular the item was.  Any idea how I can get that back?

---

### Post by forestpixie on 2007-10-21
sorry I have no idea - I haven't got votes/stars in synaptic only add/remove

---

### Post by xcusmwah on 2007-10-21
Gotcha, yeah that is where it was (add/remove).  You are awesome...thanks!

---

### Post by forestpixie on 2007-10-21
no problem

---

### Post by dedalus1904 on 2007-10-21
Just to say, I had this exact problem, stuck it into the search and got this fix immediately. I'm pretty new at Ubuntu (only just coming to realise how much can be done with it) and these forums are just about the best thing going as far as I can see. Thanks a lot guys.

---

### Post by tfkroko on 2008-07-05
> **forestpixie said:**
> sorry I have no idea - I haven't got votes/stars in synaptic only add/remove
This also helped after the better part of a day trying to access 
synaptic.  Thank you forestpixie

tfkroko

---

