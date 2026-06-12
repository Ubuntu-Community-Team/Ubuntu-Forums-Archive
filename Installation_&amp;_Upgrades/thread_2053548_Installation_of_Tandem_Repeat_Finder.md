---
title: "Installation of Tandem Repeat Finder"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by fa18 on 2012-09-05
Can anyone help me install this program: Tandem Repeat Finder program on the website below on linux:
[http://tandem.bu.edu/trf/trf404.linux64.download.html](http://tandem.bu.edu/trf/trf404.linux64.download.html)

I issued the following command via the command line but not still not making any head way:
 
1. downloaded the file
2. sudo mv trf404.linux64 /usr/local/bin
3. trf404.linux64

the message i get is: permission denied. wondering what the problem is.

---

### Post by ajgreeny on 2012-09-05
Is the file executable? Have a look with nautilus or command ```
ls -l /usr/local/bin/trf404.linux64
``` and if not make it so with ```
sudo chmod =x /usr/local/bin/trf404.linux64
```then try to run it again.

From the download page:-
> **Installation Instructions:**

 It is recommended that you copy the downloaded binary to one of the directories in your computer's path or define an alias for the program containing the fully qualified path and file name. [COLOR=Red]Once this is done, verify that the mode of the file is set to executable.[/COLOR] For details on how to use the program please refer to our [Unix Version Help]("http://tandem.bu.edu/trf/trf.unix.help.html") page. 


---

