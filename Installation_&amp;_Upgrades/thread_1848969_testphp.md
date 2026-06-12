---
title: "testphp"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by jmklein2 on 2011-09-23
I am a newbee ):P  .  I recently downloaded/installed Ubuntu server then installed the LAMP stack.  Everything seems to be working fine except a few things.  I think they are all related to this issue.  I created a symbolic link so that my home directory could be used as a website.  The testphp page works great from the default website, BUT when I try and use the [http://localhost/~username/testphp.php](http://localhost/~username/testphp.php) it requests to open the file rather than to run the file.  I created a index.html file in the same directory and it responds by displaying the page as would be expected.  I have checked the permission to the folders and files and they are 755.  I have rebooted system several times and even restarted appache with no help.  Any suggestions??

---

### Post by MAFoElffen on 2011-09-23
> **jmklein2 said:**
> I am a newbee ):P  .  I recently downloaded/installed Ubuntu server then installed the LAMP stack.  Everything seems to be working fine except a few things.  I think they are all related to this issue.  I created a symbolic link so that my home directory could be used as a website.  The testphp page works great from the default website, BUT when I try and use the [http://localhost/~username/testphp.php]("http://localhost/%7Eusername/testphp.php") it requests to open the file rather than to run the file.  I created a index.html file in the same directory and it responds by displaying the page as would be expected.  I have checked the permission to the folders and files and they are 755.  I have rebooted system several times and even restarted appache with no help.  Any suggestions??
For that to work (User's Web Directories in LAMP) the actual directory structure is /Home/username/public_html/ For example on mine it's:
/Home/mafoelffen/public_html/

To access from a browser locally, it's then file:///home/mafoelffen/public_html/index.html or [http://localhost/~mafoelffen/](http://localhost/~mafoelffen/)   I use this to build/test webpages and test javascript pluggins/extensions... and for my resume.

I think you were just missing a piece of info to do that...

---

### Post by jmklein2 on 2011-09-23
[http://192.168.2.23/~jmklein2/index.html](http://192.168.2.23/~jmklein2/index.html)  using this path works great to test my initial web page test.html.  On the ubuntu sever where the testphp.php and test.html is located doing pwd provides me with the following path /home/jmklein2/public_html.  
 
I have checked the process status, the mysql and apache are both running.  Using this same testphp.php file on the default web directory works great so I know the contents of the testphp.php file are correct to display the php status file.
 
At this point I think the ubuntu system is ):P at me to show me that it's smarter than me.  Is there any configuration files that need to be updated that I can verify?

---

