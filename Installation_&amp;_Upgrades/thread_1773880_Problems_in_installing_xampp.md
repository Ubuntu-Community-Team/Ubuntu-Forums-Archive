---
title: "Problems in installing xampp"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by floral on 2011-06-02
Hello
It has been impossible to install xampp so far. I use linux 10.04.1
I tried to install xampp with two different ways and I have problem with both.

In the first one, I followed the steps shown here : [http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377)
but when I type "su" in terminal and type in my password, i get the message "su: Authentication failure" , I stopped trying with this way.

In the second one, I followed the steps shown here : [http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=3400](http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=3400)
Through Alt+F2, I extracted the files of xampp in the /opt , the directory for xampp is : /opt/lampp/htdocs/xampp
When I type localhost in firefox, I get this message : 
> It works!
This is the default web page for this server.
The web server software is running but no content has been added, yet.,
however no page for configuration of xampp opens.
Also, the index.php file found in the htdocs directory says : 
```
<?php
    if (!empty($_SERVER['HTTPS']) && ('on' == $_SERVER['HTTPS'])) {
        $uri = 'https://';
    } else {
        $uri = 'http://';
    }
    $uri .= $_SERVER['HTTP_HOST'];
    header('Location: '.$uri.'/xampp/');
    exit;
?>
Something is wrong with the XAMPP installation :-(
```I deleted the lamp file from /opt and tried it all over again. The same result.
Also, when I type _/opt/lampp/htdocs/xampp start_ in terminal, i get a message that it did not find the directory  :roll: 
the directory is there!

Another odd thing, is that when I tried to change the permission of the htdocs - as seen in the second guide - it does not let me change them.

Why I have all these problems in installing xampp ?
My target is to install joomla, if I ever pass through this stage.

---

### Post by gordintoronto on 2011-06-02
> **floral said:**
> ...however no page for configuration of xampp opens.


It installed perfectly, and you expected something which was not going to happen. Sometimes you have to read the docs.

---

### Post by floral on 2011-06-02
What do you mean?
Which docs?
the index.php said that there "is something wrong"

---

