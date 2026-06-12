---
title: "Server install or standard?"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by timka1 on 2006-08-01
Still fiddling with the install!

I want to be able to run a web server from my ubuntu installation but I would also like to use the desktop for browsing etc at the same time.

Is it better to do a server install and import the desktop apps or the other way round? Or is this a case of "Half a dozen of one and six of the other"?

---

### Post by Dr. Nick on 2006-08-01
You can do a standard desktop install and then install apache, the standard desktop install will make sure you get loaded into a gui to start so you can use a graphical browser as opposed to a text based web browser.

The server version has  a differnet kernel, I dont know all the differences between desktop/server kernels, but I have run web servers from standard desktop kernels in the past without issue.

but in the end it probably doesnt really matter which way you do it.

---

### Post by SeanHodges on 2006-08-01
Desktop install would be less hassle, you'll get all the desktop apps etc. As Dr. Nick said, theres not much to worry about as they both use the same repositories.

Is the apache install for development testing, or will it be live?

---

### Post by timka1 on 2006-08-01
Thanks Dr Nick and Mr Hodges.

In answer to the question whether it'll be used in production or development: it's basically in between because it'll probably be for a personal website which because my ISP provides a static IP address can be served from my home computers using my own internet connection which is one of the main reasons I'm with them.

Is there any mileage in installing both in different partitions and see how I get on with both and then decide later?

Looks like I'm might end up with another box to act as a server: my wife'll kill me!:lol:

---

### Post by SeanHodges on 2006-08-01
I think a standard Desktop install will get you where you need to go. Use that to set up and build your website (it can act as the live webserver as well to start with). Make sure everything works, then buy an old cheap PC on eBay and install the server version on it - this is where the Server install is better, as it is much more efficient on slow machines. Transfer your website to this "Server" PC, and make that the live one.

This way, you can play around with your website on your main PC, but not worry about breaking the live version ;)

Hope this helps,

Sean

---

### Post by az on 2006-08-01
The LAMP stack does not interfere with the Desktop packages and vice versa.  The only reson to not run both at the same time is to respect best security practices.

For practical reasons, it takes less time to install using the Desktop cd and then install LAMP (apache2 php5-mysql libapache2-mod-php5 mysql-server)

You should be done in about 25 inutes.  If you install the server, it takes about that long just to unpack the base system.  Unpacking the desktop packages will take just under another hour.

Don't use the server kernel on a desktop.  The desktop kernel will work fine on a server.  If you need it to be more optimised, you wouldn't be running a desktop on it, right?

---

### Post by timka1 on 2006-08-01
Makes a lot of sense. Thanks for the advice: the forums really are as good as they are cracked out to be!

---

