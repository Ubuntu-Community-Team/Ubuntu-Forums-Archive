---
title: "Ubuntu software center not connecting to internet"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by Friwise on 2011-10-18
Hi all!!
I am running Ubuntu 11.10 for the last few days and everything was perfect until yesterday when my Ubuntu Software Center showed problems with connection to the internet.
Now, I cannot install any application because of that.
I have good wireless connection and other internet applications work. Moreover, when I disconnect (on purpose) from the internet I don't even have the option to install any application. When I am connected I have this option but after I push the install button it tells me that I shall check my internet connection.
Any suggestion?
Thanks in advance

---

### Post by 2F4U on 2011-10-18
Does the installation in a terminal using apt-get work?

---

### Post by Friwise on 2011-10-18
I can normally install from terminal!

---

### Post by Friwise on 2011-10-19
Moreover, now I am connected through wire connection and still it shows me the same error message when I try to install anything from Ubuntu software center

---

### Post by matt_symes on 2011-10-19
Hi

What is the exact error message?

Open a terminal and type 

```
software-center
```Try to install some software. Post back an error messages from the terminal using copy and paste.

Kind regards

---

### Post by Friwise on 2011-10-19
**_software-center_** gave me this:

2011-10-19 09:19:37,346 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-10-19 09:19:38,149 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-10-19 09:19:38,225 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css


**_Then I tried to install a software called calibre and got this:_**

2011-10-19 09:20:50,076 - softwarecenter.backend - ERROR - error in _on_trans_finished '&#931;&#966;&#940;&#955;&#956;&#945;: None
None

'
2011-10-19 09:20:54,126 - softwarecenter.backend - ERROR - error in _on_trans_finished '&#931;&#966;&#940;&#955;&#956;&#945;: &#913;&#960;&#945;&#953;&#964;&#949;&#943; &#964;&#951;&#957; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#956;&#951;-&#941;&#956;&#960;&#953;&#963;&#964;&#969;&#957; &#960;&#945;&#954;&#941;&#964;&#969;&#957;
&#919; &#949;&#957;&#941;&#961;&#947;&#949;&#953;&#945; &#945;&#965;&#964;&#942; &#952;&#945; &#967;&#961;&#949;&#953;&#945;&#950;&#972;&#964;&#945;&#957; &#964;&#951;&#957; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#960;&#945;&#954;&#941;&#964;&#969;&#957; &#945;&#960;&#972; &#956;&#951;-&#960;&#953;&#963;&#964;&#959;&#960;&#959;&#953;&#951;&#956;&#941;&#957;&#949;&#962; &#960;&#951;&#947;&#941;&#962;.

calibre calibre-bin libchm1 libpodofo0.9.0 libqt4-help libqt4-scripttools libqt4-test libqtassistantclient4 python-beautifulsoup python-cherrypy3 python-cssutils python-cssutils-doc python-django python-django-tagging python-dnspython python-encutils python-lxml python-pyparsing python-qt4 python-routes python-sip python-webob'

---

### Post by matt_symes on 2011-10-19
Hi

> 
&#931;&#966;&#940;&#955;&#956;&#945;: &#913;&#960;&#945;&#953;&#964;&#949;&#943; &#964;&#951;&#957; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#956;&#951;-&#941;&#956;&#960;&#953;&#963;&#964;&#969;&#957; &#960;&#945;&#954;&#941;&#964;&#969;&#957;
&#919; &#949;&#957;&#941;&#961;&#947;&#949;&#953;&#945; &#945;&#965;&#964;&#942; &#952;&#945; &#967;&#961;&#949;&#953;&#945;&#950;&#972;&#964;&#945;&#957; &#964;&#951;&#957; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#960;&#945;&#954;&#941;&#964;&#969;&#957; &#945;&#960;&#972; &#956;&#951;-&#960;&#953;&#963;&#964;&#959;&#960;&#959;&#953;&#951;&#956;&#941;&#957;&#949;&#962; &#960;&#951;&#947;&#941;&#962;.=>
> 
Error: Requires the installation of non-trusted packages
 This will need to install packages from non-certified sourcesFrom [https://answers.launchpad.net/ubuntu/+source/software-center/+question/170791](https://answers.launchpad.net/ubuntu/+source/software-center/+question/170791)
> 
[Ian Ace (iaculallad)]("https://launchpad.net/%7Eiaculallad")          said     on 2011-09-11:      #3       System > Administration > Update Manager > Settings
 On the Software Sources window, click on the Ubuntu Software tab.  Under Downloadable from the Internet, put a check on Source Code.
 HTH.

> [Scott Barras (sjbarras)]("https://launchpad.net/%7Esjbarras")          said     on 2011-09-13:      #5   
    Thanks Ian Ace, that solved my question.


Hopefully that will also work in 11.10

Kind regards

---

### Post by Friwise on 2011-10-19
In my laptop it Source Code was already checked.
So, the problem does not come from this.

P.S: All the options are checked. Should I only have Source Code checked?

Somebody from the ubuntu.gr forum helped me to solve this. The problem was solved by choosing Download from: Main Server

---

### Post by xSkApOnEx on 2012-02-10
*bUmP*

---

### Post by supermatti on 2012-02-12
> **Friwise said:**
> Hi all!!
I am running Ubuntu 11.10 for the last few days and everything was perfect until yesterday when my Ubuntu Software Center showed problems with connection to the internet.
Now, I cannot install any application because of that.
I have good wireless connection and other internet applications work. Moreover, when I disconnect (on purpose) from the internet I don't even have the option to install any application. When I am connected I have this option but after I push the install button it tells me that I shall check my internet connection.
Any suggestion?
Thanks in advance

> **Friwise said:**
> I can normally install from terminal!

> **Friwise said:**
> In my laptop it Source Code was already checked.
So, the problem does not come from this.

P.S: All the options are checked. Should I only have Source Code checked?

Somebody from the ubuntu.gr forum helped me to solve this. The problem was solved by choosing Download from: Main Server

Error: Requires the installation of non-trusted packages
 This will need to install packages from non-certified sources                                 From [https://answers.launchpad.net/ubuntu...uestion/170791]("https://answers.launchpad.net/ubuntu/+source/software-center/+question/170791")
     Quote:
                                                 [Ian Ace (iaculallad)]("https://launchpad.net/%7Eiaculallad")          said     on 2011-09-11:      #3       System > Administration > Update Manager > Settings
 On the Software Sources window, click on the Ubuntu Software tab.   Under Downloadable from the Internet, put a check on Source Code.
 HTH.

i have the same problems, but couldn,t  solve then as shown above by Ian Ace,
please, can somebody help me, i am new in ubuntu11.10, but know quiet well the 9.10


thanks a lot:KS

supermatti

pd:  maybe it's important to mencion that i installed from a usb-drive, i ran upgrade, and i managed to actualize

---

### Post by supermatti on 2012-02-16
solved... with main server it works

---

