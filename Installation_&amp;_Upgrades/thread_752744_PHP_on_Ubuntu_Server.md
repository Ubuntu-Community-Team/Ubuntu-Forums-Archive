---
title: "PHP on Ubuntu Server"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by guitarman on 2008-04-11
Hi all, I have been trying to add a page on my site that runs on my Ubuntu server that will allow users to text me on my cell phone. However page runs in PHP so I installed it but when I load that page, the page loads, but the security code that is suppose to generate a security code with the monofont.ttf never seems to come up.  So I created another small file to run the following so I can see what php is running: 

<?php
print_r (phpinfo());
?>


but get the following:
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/test2.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

Can anyone explain if I did not install PHP properly?

To understand the page that I was trying to create, go to : [www.easykiss123.com](www.easykiss123.com) and look at the SMS Texting video.  I have been having problem with the security code appearing on the page when you run it, so when you hit the submit button, I get an response that the security code is incorrect, so I take it that the PHP file does generate the code, but does not display it.  I emailed the webmaster of easykiss123, but got no response.  I guess that they are not as responsive as the Ubuntu Forums.:)


Any help would be greatly appreciated.

thanks

---

