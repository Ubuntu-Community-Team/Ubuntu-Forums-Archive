---
title: "apache2 problem"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by mac73 on 2006-07-20
helo guys

i hv installed apach2, mysql and php5 but i m not geting apache started.

 basically i want to install sterber(s/w 4 project management.
 4 this i want all these things running.

pls........ help me out

tnx.

---

### Post by DoorGunner on 2006-07-20
what does [http://localhost](http://localhost) give you ??

---

### Post by mac73 on 2006-07-20
it is givin me followin


you hv chosen to open


which is PHTML file
from :http//localhost


and akin 4 savin file

---

### Post by DoorGunner on 2006-07-20
I have a coulple of things for you to try

1.   If it is giving you something back it apache may be working. Is there any files or folders in your /var/www file? 

2.   Have you tried $ sudo gedit /var/www/testphp.php file?
all you need to do is put 
<?php phpinfo(); ?> 
into the file and save it.....go back to and try [http://localhost/testphp.php](http://localhost/testphp.php)

this will confirm that apache and php5 are working. I am just trying to see what is working at this point.

---

