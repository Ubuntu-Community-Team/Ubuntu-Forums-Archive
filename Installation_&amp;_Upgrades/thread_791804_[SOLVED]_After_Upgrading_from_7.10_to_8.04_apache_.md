---
title: "[SOLVED] After Upgrading from 7.10 to 8.04 apache is messed up."
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by jeff.sadowski on 2008-05-12
First I tried my install of phpmyadmin after the upgrade
and firefox askes if I want to download a file (explained more in detail below)
then I tried going to the main page 127.0.0.1
and I get as expected "It worked" as the /var/www/index.html
page is the default.
I tried moving /var/www/index.html to /var/www/index.php and changed the message a little to see if it would work. then I got the download message in firefox again. I thought there was a problem in php so i tried reinstalling php. hmm php4 doesn't exist I'll try php5 ok that installed same results from firefox it askes to download a file.

Reading some I thought I needed a fresh install of apache
I tried uninstalling apache like so
apt-get remove --purge apache2.2-common (without this it did not reinstall /etc/apache2 directory because I delete that to make sure configs where installed correctly)
apt-get remove --purge apache2
apt-get remove --purge php5
apt-get autoremove
apt-get clean

I tried connecting with firefox to 127.0.0.1 and I still go a response it asked me if I wanted to download a file. WTF is going on?
I did lsof |grep IP
and saw kio_http was running on port 80
so I killed it as follows
killall -9 kio_http
What is kio_http and why was it running? (I couldn't find out why)
I checked again with firefox and I get expected can not connect message.
Then I install apache like so

apt-get install apache2

I see that /var/www was still without index.html and still had index.php
so I moved it back to index.html
hopping for a fresh install I go to 127.0.0.1 with firefox and to my surprise I get 

You have chosen to open

which is a PHTML file
<> open with [Browse...]
<> Save to Disk
[] Do this automatically for files like this from now on.

(aka the download message)
I check to see that kio_http wasn't running and that apache is (it was correct) then
I check /var/www/index.html and it looks normal
I have no idea what apache is trying to dish out and how it got so screwed up.

I would like to get back to a working phpmyadmin.
But first I need a working web server. then a working ssl server then
one that works correctly with php then I can get phpmyadmin reinstalled.
Why is it so hard?
I would have better luck installing from source but I want to know what I did wrong? and what is going on?
Any clue on what to try next?

***update firefox is mostly the culprit
I tried again whith apache uninstalled and am still getting the same thing in firefox.
I disbelieved firefox and tried telnet to 127.0.0.1 port 80 and it failed hmm
I then tried konqueror and it worked  correctly so half way there.
***update php worked after installing 
php5-cgi
and php5-cli
*** update got ssl working thanks to
[https://launchpad.net/ubuntu/+source/apache2/+bug/77675](https://launchpad.net/ubuntu/+source/apache2/+bug/77675)
particularly

 maraja wrote on 2008-04-30: (permalink)

setup

   1. sudo apt-get install apache2
   2. sudo apt-get install openssl
   3. sudo apt-get install ssl-cert

create ssl certificate:
sudo make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/ssl/private/localhost.pem

switch to apache sites configuration:
cd /etc/apache2/sites-available/

bakup the default configuration:
sudo cp default default.backup.date

be sure to listen the port 80 for the default:
sudo sed -i '1,2s/\*/*:80/' default

create the ssl configuration:
sudo cp default ssl

set the ssl port:
sudo sed -i '1,2s/\*:80/*:443/' ssl
sudo sed -i "3a\\\tSSLEngine On\n\tSSLCertificateFile /etc/ssl/private/localhost.pem" ssl

enable ssl:
sudo a2ensite ssl
sudo a2enmod ssl

restart apache2:
sudo /etc/init.d/apache2 restart

=)
So there was a bug the above should be made into a script
*** and finally I got phpmyadmin working. I didn't bother installing it the apt-get way it is just a page and really easy to install
I needed to uninstall php5-mysql and reinstall it then
I was able to unpack the phpmyadmin stuff and edit the file
sudo cp /var/www/phpMyAdmin-2.11.5.1-all-languages-utf-8-only/config.sample.inc.php /var/www/phpMyAdmin-2.11.5.1-all-languages-utf-8-only/config.inc.php
sudo gedit /var/www/phpMyAdmin-2.11.5.1-all-languages-utf-8-only/config.inc.php
change
$cfg['blowfish_secret'] = ''; /* YOU MUST FILL IN THIS FOR COOKIE AUTH! */
to
$cfg['blowfish_secret'] = 'test'; /* YOU MUST FILL IN THIS FOR COOKIE AUTH! */
test could be anything I suggest not to make it a valid password then it will ask for a username and password.

---

### Post by GurneyHalleck on 2008-06-01
I'm also getting download prompts in Firefox 3 after installing Apache 2.0 and PHP 5.

Did you ever work out why Firefox was trying to download certain pages instead of display them?

---

### Post by GurneyHalleck on 2008-06-02
After searching for answers on the web, I found the solution.

Clear your cache in Firefox, and suddenly the download prompt doesn't appear anymore.

---

