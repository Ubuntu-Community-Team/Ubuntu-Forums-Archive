---
title: "problem in installing ilias (learning management system) on ubuntu"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2011-02-04
I am trying to install a learning management system known as ilias on a Ubuntu 10.04 server edition.

Download ilias-4.1.4.zip from

[http://www.ilias.de/docu/](http://www.ilias.de/docu/)  
 > [COLOR=#222222][SIZE=2]apt-get install php5-imagick [/SIZE][/COLOR]     imagemagick       [COLOR=#222222][FONT=monospace][SIZE=2]  Memory limit in /etc/php5/apache/php.ini[/SIZE][/FONT][/COLOR]
 [COLOR=#222222][FONT=monospace][SIZE=2]    changed to as follows (from default)[/SIZE][/FONT][/COLOR]
> 
[COLOR=#222222][FONT=monospace][SIZE=2]memory_limit = 80M   [/SIZE][/FONT][/COLOR] 
 [COLOR=#222222][FONT=monospace][SIZE=2]    aptitude install php5-gd[/SIZE][/FONT][/COLOR]
have a databse ilias.Then       [http://www.ilias.de/docu/ilias.php?ref_id=367&obj_id=23476&cmd=layout&cmdClass=illmpresentationgui&cmdNode=e&baseClass=ilLMPresentationGUI&obj_id=6531](http://www.ilias.de/docu/ilias.php?ref_id=367&obj_id=23476&cmd=layout&cmdClass=illmpresentationgui&cmdNode=e&baseClass=ilLMPresentationGUI&obj_id=6531)
      as per above link I go to /etc/php5/apache2/php.ini
     and do  
> [COLOR=#222222][FONT=monospace][SIZE=2]suhosin.session.encrypt=Off
    suhosin.post.max_vars=10000
    suhosin.request.max_vars=10000[/SIZE][/FONT][/COLOR]
 [This link]("http://www.ilias.de/docu/ilias.php?ref_id=367&obj_id=29985&obj_type=PageObject&cmd=layout&cmdClass=illmpresentationgui&cmdNode=e&baseClass=ilLMPresentationGUI") has installation instructions.I install every thing and then it succesfully finishes.
Then I try to go to home page as 

[http://192.168.43.129/ilias/](http://192.168.43.129/ilias/)
but I get error
> Fatal Error: ilInitialisation::initClientIniFile called             without CLIENT_ID.Can any one help here?

---

