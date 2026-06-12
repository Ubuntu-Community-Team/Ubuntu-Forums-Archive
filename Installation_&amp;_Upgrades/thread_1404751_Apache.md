---
title: "Apache"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by scriptsit on 2010-02-11
Salvete omnes,

I have an issue that few people are probably going to want to help me with. I'm trying to configure apache on my present system so that I can run perl cgi programs locally. I feel like my perl is developing well, but I've reached a plateau, and wish to go further by learning cgi programming. 

The problem is, I can't seem to get any of the example programs to work. After a bit of research, it seems that I need to configure my apache to recognize cgi scripts. I've tried numerous places, but all of the explanations go over my head as I am still a novice linux user. I know how to compile a C program, mkdir, cd, ls, cat ... and then we're stretching my capabilities. I continue to learn every day, and have bought a few books which are helping me get there. I even bought an apache book, but it's not helping me much. 

My question: can someone help me set up apache at least to the point where I can run cgi scripts? Assume that I have done nothing further than: sudo apt-get install apache2.

I don't even have a cgi-bin dir yet as I don't know where these belong, or how to do a script-alias. 

If someone could help me with this favor I'd be most grateful.

---

### Post by Satoru-san on 2010-02-11
You need to add something like this to your sites file. I am not sure where it is in ubuntu.

This is mine, you can use it but I would make it work for you.
```
<IfModule alias_module>
    ScriptAlias /cgi-bin/ "/var/www/localhost/cgi-bin/"
</IfModule>

# "/var/www/localhost/cgi-bin" should be changed to whatever your ScriptAliased
# CGI directory exists, if you have that configured.
<Directory "/var/www/localhost/cgi-bin">
    AllowOverride None
    Options None
    Order allow,deny
    Allow from all
</Directory>

```

---

### Post by scriptsit on 2010-02-11
Satoro,

I appreciate your response, and I've seen similar things while searching for an answer elsewhere. My question to you is where to put said command. Also, where do I put cgi-bin folders? One is apparently in the '/' directory. Is that right? And the other would be in /var/www/this_place ?

---

### Post by Satoru-san on 2010-02-11
I am not sure the exact structure of ubuntu apache, it has been a while since I used it. the file you need to put that in is around /etc/apache2/sites/ 

you need to add the cgi-bin folder to your site in your /var/www so  you would put that folder in /var/www/<your site>/

EDIT: I think that ubuntu apache doesnt have a site folder. I guess you could either change that in your site config file and make a <your site> folder then create an htdocs folder along with your cgi-bin your you can make a new folder in your /var/ folder.

Good luck.

---

