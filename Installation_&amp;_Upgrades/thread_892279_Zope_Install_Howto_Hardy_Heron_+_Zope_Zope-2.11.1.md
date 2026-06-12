---
title: "Zope Install Howto: Hardy Heron + Zope Zope-2.11.1"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by mojoheader on 2008-08-17
I recently had to setup a Hardy Heron image with a Zope installed for a development project.

 I have done this many times in Debian (and RH/Fedora for that matter), but ran across some weirdness with Heron, so I thought I woudl share my experience that i may hekp someone else.

 The best guide I found was the Zope-2.11.x-final/doc/INSTALL.txt 
but the Zope installation page is also somewhat helpful for general compiler & configuration issues:
  [http://www.zope.org/Documentation/Books/ZopeBook/2_6Edition/InstallingZope.stx](http://www.zope.org/Documentation/Books/ZopeBook/2_6Edition/InstallingZope.stx)

 ... but there is nothing specific to Unbuntu, so you may run into compile errors that are not that obvious, like I had involving the AccessControl.so lib.

 Here is how I set it up:

1. Ensure you have Python 2.5.x installed:
 $ python --version
Python 2.5.2

If not, install it:
 apt-get install python2.5-dev 

2. Download the Zope 2.11.1 tarball:
 [http://www.zope.org/Products/Zope/2.11.1/Zope-2.11.1-final.tgz](http://www.zope.org/Products/Zope/2.11.1/Zope-2.11.1-final.tgz)

3. Install the GNU C Library (Development Libraries and Header Files): 
sudo apt-get install libc6-dev

4. Unpack the Zope tarball to a [new] directory:
 tar zxvf Zope-2.11.1-final.tgz

5. cd to the [new] directory, then run:
 sudo ./configure --prefix=/var/www [prefix is optional, just note where Zope is being configured by default (usually under /opt)

6. Now run:
sudo make, 

7. Then:
sudo install

8. Then:
 sudo /var/www/bin/mkzopeinstance.py

 * When prompted for a Zope install directoy:
"Please choose a directory in which you'd like to install
Zope "instance home" files such as database files, configuration
files, etc."
 ... type an easy to remember directory (I used /var/www/zopehome).

9. Answer the initial username and password prompts as needed (remember these!)

*** You are done with the build & install part!

10. Now, test the install by starting your new Zope instance by changing to the new instance home directory created and executing zopectl:
 /<your zopehome>/bin$ sudo ./zopectl start

 You will be promtpted for the admin user password (as you created above).
Once autheticated the Zope daemon will start and return a confirmation:
"daemon process started, pid=<some PID>"

 If you get an error at this point, verify your zopehome/bin folder exists and that the deamon controller "zopectl" is present.

11. Finally, open a browser and navigate to http://<local ip address>:8081
You should be greeted with the Zope general information page.

 If you're impatient (like me), go straight to the administration page:
http://<local ip address>:8081/manage

 You will be prompted for admin credentials:
 username: admin
 password: whatever you entered in step 9 (above)

 Voila! The Admin page opens at the Zope Root Folder.
 
 Again, the best guide I found was the Zope-2.11.x-final/doc/INSTALL.txt 
but the Zope installation page is also somewhat helpful for general compiler & configuration issues.

 HTH and Happy Zoping!

---

### Post by nalioth on 2008-08-29
The following two items are really big security risks.  'Sudo' is not needed for either "./configure" or "make".  Any miswritten or malformed code in these can potentially wipe your box.

> **mojoheader said:**
> 
5. cd to the [new] directory, then run:
 sudo ./configure --prefix=/var/www [prefix is optional, just note where Zope is being configured by default (usually under /opt)

6. Now run:
sudo make,

Isn't the following supposed to be "sudo make install"?
I would give [checkinstall](http://www.asic-linux.com.mx/~izto/checkinstall/index.php) (available in the repos) a run first, for easier package management.  If [checkinstall](http://www.asic-linux.com.mx/~izto/checkinstall/index.php) doesn't work, you can always run with 'make install'.
> **mojoheader said:**
> 
7. Then:
sudo install 


Thanks for the writeup, and remember:  You can never be too secure.  One should only use 'sudo' when absolutely required, not as a default precedent.

---

### Post by rugbert on 2008-10-09
can either of you two help me with my zope problem where its not loading after a migrations?

[http://ubuntuforums.org/showthread.php?t=940064&highlight=zope](http://ubuntuforums.org/showthread.php?t=940064&highlight=zope)

---

