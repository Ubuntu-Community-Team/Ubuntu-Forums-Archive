---
title: "php5-curl problem"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by zazbar on 2007-07-03
Hi all,

I have a small problem on my ubuntu edgy .....

i use the php5-cli to execute commands.

Under root, i have :

```
~# php -r 'phpinfo();' | grep -i curl
curl
CURL support => enabled
CURL Information => libcurl/7.15.4 OpenSSL/0.9.8b zlib/1.2.3 libidn/0.6.3
~#
```


```

~# php -r 'curl_init("http://www.google.fr");'
~#
```


And as my normal user, i am doing :
```

~$ php -r 'phpinfo();' | grep -i curl
~$

```

```

~$php -r 'curl_init("http://www.google.fr");'

Fatal error: Call to undefined function curl_init() in Command line code on line 1
~$

```
I have curl (Curl, libcurl3, php5-curl) installed.

Anyone have any idea where it can come from ??? and how can i make work php and curl for my user ?

Thanks in advance !

---

### Post by zazbar on 2007-07-03
I solved my problem ..
The file /etc/php5/cli/php.ini was only readable by root ..... so my user didn't load extensions ....
I never changed permissions on this file ... and on another computer the rights were good ...

So i don'tknow why this installation was like that ....

---

### Post by ntom-taylor on 2007-07-11
Hello, 

I'm not sure how exactly you have installed curl?  I just wrote this quick little 'how to' on installing curl for ubuntu and php5, it might help ? [click here to see the how to ]("http://www.theatons.com/blog/2007/07/10/ubuntu-install-setup-curl-for-php-php5/")

Tom

Edit: Just saw your post saying you solved it, oh well the link still might help others ?

---

### Post by maudmoonshine on 2007-10-23
>  
oh well the link still might help others ? 

 
It sure has; been searching for 2 days on how to install cURL.
 
I obviously don't know how to search here properly... yet.
 
Now all I need is to figure out how to get PHP Output Buffering (gzip) to install/work. Guess that'll be another several days searching... ;-)))
 
Thanks again for your Howto.
 
Latter: Output Buffering only took 5 mins to find the solution; which it simply editing PHP.ini (I hope I've edited the right copy as there are several choices in various directories?) and switching output_buffering to On.

---

