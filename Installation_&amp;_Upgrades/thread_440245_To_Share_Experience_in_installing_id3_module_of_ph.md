---
title: "To Share Experience in installing id3 module of php"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by challengerlks on 2007-05-11
May be there is someone already done it before. But I also want to share my experience to install id3 module in php successfully. I hope it can help.

Pre-requisite: php source code ( in my case, I used php5, so it's located /usr/include/php5)

1. First: get the source code of id3 module form [http://pecl.php.net](http://pecl.php.net) ( U can type "id3" in their search engine)

2. Extract the zipped file in the source code of extensions of php ( in my case, it's /usr/include/php5/ext/ ) and package.xml as well

3. then type "pecl build" under /usr/include/php5/ext

4. A procedure would be invoked and it would ask U whether U want to enable id3, then U just press "enter" to represent autodect

I think the following  procedures are just redundant, but there is no harm to repeat  those.

5. change the directory into PHP_SOURCE/ext/id3-x.y (depends on your version downloaded from pecl )

6. Type "sudo make".

7. It would tell you that the libaries were build under "module" directory

8. Type "sudo make install"

9. It would say the id3.so had be copied to the directory of your php engine ( remember : not the source code )

This follwoing must be done not matter whether U follow the above redundant procedures :

10. Add "extension=id3.so" into php.ini of your php engine

11. Restart apache server

Then , it's done

---

