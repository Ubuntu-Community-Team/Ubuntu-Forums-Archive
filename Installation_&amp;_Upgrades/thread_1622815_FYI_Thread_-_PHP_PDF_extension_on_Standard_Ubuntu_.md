---
title: "FYI Thread - PHP PDF extension on Standard Ubuntu install"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by dazman19 on 2010-11-15
Hi,

I have spent absolutely hours trying to get my pdf extensions installed for my development PHP/Apache2 server working. Since I couldn't find a useful thread, here is a quick HOWTO once over. To save someone else some time.

After fresh install Ubuntu 10.10 Maverick

Install apache2 (via synaptic or package manager)

[PHP]sudo apt-get install apache2[/PHP]

install php

[PHP]sudo apt-get install php5[/PHP]

For those who don't know 9/10 the package manager will make your apache directory: /etc/apache2 (this is where apache2.conf and an empty httpd.conf file is located) NOTE That your apache2.conf is actually the file the server is using for the settings.
And php will be /etc/php5/apache2/ (this is where php.ini is located)

To load the PDF extension.
 [PHP]
wget http://www.pdflib.com/binaries/PDFlib/801/PDFlib-8.0.1p8-Linux-php.tar.gz /tmp

[/PHP]
NOTE: this is for x86 not x64 you can find the download page here:
[http://www.pdflib.com/download/pdflib-family/pdflib-8/](http://www.pdflib.com/download/pdflib-family/pdflib-8/)

after unpacking the tarball

[PHP]/tmp$ sudo tar -xzvf PDFlib-8.0.1p8-Linux-php.tar.gz [/PHP]

This will create a bind and doc directory. 

under /tmp/PDFlib-8.0.1p8-Linux-php/bind/php/

php-510             
php-520             
php-520mt           
php-530             
php-530mt   

There will be some sub dir's php-530 is for php5.30 etc... the mt directories are for multithreading servers. 

To check if your server is multithreading and what version of php you have you can run a test script from your /var/www/ folder. just make a file called phpinfotest.php and put this in it:
<?php phpinfo() ?>

then open the page [http://localhost/phpinfotest.php](http://localhost/phpinfotest.php)

It will be quite likely that you won't be using multi threading. 

Anyhow, copy the libpdf_php.so to your extensions directory. (this is where I got lost because for some strange reason it was NOT /etc/php5/apache2/ext/ or something simple. This folder is located under the /usr/lib/php5/(some date like 20090626+lfs) in my case.

[PHP]sudo cp /tmp/PDFlib-8.0.1p8-Linux-php/bind/php/php-530/libpdf_php.so /usr/lib/php5/20090626+lfs/[/PHP]

Add the extension to your php.ini and you are done.
[PHP]
sudo gedit /etc/php5/apache2/php.ini
[/PHP]

add this like to where the extensions are
extension=libpdf_php.so

save & close. 

restart apache2.

[PHP] sudo /etc/init.d/apache2 restart[/PHP]

Test its working by running your phptestinfo.php again in your browser. If you can find something like:

PDF Support        enabled
PDFlib GmbH Binary-Version         8.0.1p8
PECL Version         2.2.0
Revision         $Revision: 1.20.2.2 $

then you know it has enabled.

I really hope this helps someone out there..... 

Daz

---

### Post by shadowofblood on 2010-11-15
That's some great information! :P

But shouldn't this be in the tutorial section? :confused:

---

### Post by dazman19 on 2010-11-15
Yeh sorry, I have no idea that existed this forum is massive. I am happy for a moderator to move it.

---

### Post by levidurfee on 2011-06-24
That was very helpful, thank you!

However, I'm getting this error

> Fatal error: Uncaught exception 'PDFlibException' with message 'Function  must not be called in 'object' scope' in /var/www/temp/pdf/test.php:7 Stack trace: #0 /var/www/temp/pdf/test.php(7): pdf_begin_page(Resource id #2, 595,  842) #1 {main}   thrown in /var/www/temp/pdf/test.php on line 7 

When I try to use this code:

> <?php
// create handle for new PDF document
$pdf = pdf_new();
// open a file
pdf_open_file($pdf, "philosophy.pdf");
// start a new page (A4)
pdf_begin_page($pdf, 595, 842);
// get and use a font object
$arial = pdf_findfont($pdf, "Arial", "host", 1); pdf_setfont($pdf, $arial, 10);
// print text
pdf_show_xy($pdf, "There are more things in heaven and earth, Horatio,",50, 750); 
pdf_show_xy($pdf, "than are dreamt of in your philosophy", 50,730);
// end page
pdf_end_page($pdf);
// close and save file
pdf_close($pdf);
?>

---

