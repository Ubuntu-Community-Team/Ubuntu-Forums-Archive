---
title: "PHP and Apache Root problems"
date: 2005-05-26
forum: Installation &amp; Upgrades
---

### Post by khansen on 2005-05-26
I've been running Ubuntu as a regular server for quite some time now.  

I recently went  throught a series of updates and had to reinstall Apache2.  In the process, php files stopped being parsed.  Calling them in the browser would pop up a "What do you want to open this with?" dialog.  I went through all the steps to reinstall and configure php with apache as I had done in the past.  Something strange is happening, however.  For some reason, any php filein /var/www will not be parsed, but any .php file in the userdir's (/home/username/public_html) is.  I can't figure this one out for the life of me.   ](*,)  ](*,) 

Any help would be greatly appreciated.

---

### Post by Sleeper Service on 2005-05-26
Is it a permissions thing?  I've been caught out by permissions before after backing up and later unpacking.  Make sure the php files are at least readable by anybody...

---

### Post by khansen on 2005-05-26
[QUOTE=Sleeper Service]Is it a permissions thing?  I've been caught out by permissions before after backing up and later unpacking.  Make sure the php files are at least readable by anybody...[/QUOTE]

Thanks for the suggestion, It was something I hadn't thought of.  However it didn't solve the problem.   

some other strange things:[list]
[*]I can access .html files with no problem.
[*]Accessing the php files directly no longer pops up an error.  I just get a blank page with some html code, which is the straight html code not parsed by php.  It's like it reads the file, strips out all the php and returns what is left.
[/list] 

Would it be best at this point to try removin then re-installing Apache2, php, and all the rest?  What other options are there to try?

---

### Post by khansen on 2005-05-26
Thank you all for the suggestions.  It turns out it was a PHP/Mysql issue.  After browsing about a million other forums, I came across one [Here](http://ubuntuforums.org/showthread.php?t=18514&highlight=Call+undefined+function%3A+mysql_connect%28%29) 
that mentioned uncommenting a line in my /etc/php4/apache2/php.ini file.  This is the line.
extension=mysql.so

I don't know if this is the best way to solve it, but it worked for me.

---

### Post by Sleeper Service on 2005-05-27
Glad you've fixed it :)

---

