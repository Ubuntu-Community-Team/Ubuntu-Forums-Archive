---
title: "A number of beginning questions ..."
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by rlynwood on 2007-04-20
Hello,

I have a standard Edgy installation on a small hdd and have a larger hdd that I want to keep all my data on.  My first question is, can I move the /home file to the main data hdd, and, of course, how to to that?

My second two questions are, where are my desktop settings and Firefox and Opera bookmarks stored?

Finally, if I've missed obvious sources of information, where should I have looked in the Ubuntu Wiki and/or Forums?

Ray

---

### Post by bukwirm on 2007-04-20
For the second question, most settings form applications are stored in "dot files" (or directories) in your home directory - that is, a file/directory called something like this: ".mozilla" . These files/directories are hidden by default - you can change some setting somewhere in Nautalis to make them visible.

Firefox stores it's bookmarks somewhere in your .mozilla directory. It also has an export feature which allows you to save your bookmarks in a form which can be imported into other browsers.

I haven't used Opera, but I assume it behaves in a similar manner.

---

### Post by spin2cool on 2007-04-20
I usually leave my home directory on my root partition and just create links from inside it to my data partitions.  So if my data partition is located at /media/data, l go to my home directory and type:

'ln -s /media/data data'

Firefox profiles:  ~/.mozilla/firefox/

Not sure about opera - is there a '.opera' folder in your home directory?  try 'find /home/username/ -name *opera*'

---

### Post by spin2cool on 2007-04-20
See also this thread:
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

or search the forum for "move home directory'

---

### Post by rlynwood on 2007-04-20
Spin2cool,

Thanks for your answer.  In fact, thanks to everyone for their answers.  I expect to repsond to all of them as my underestanding makes it appropriate.

"I usually leave my home directory on my root partition and just create links from inside it to my data partitions. So if my data partition is located at /media/data, l go to my home directory and type:  'ln -s /media/data data'"

Is this partition on the same hdd as your /home directory is on?  My intention is to put all my data on a separate hdd so I can play with different distros on one hdd and, while in each of them, have access to my data.  Ideally, since I expect to be storing articles and information in that data hdd frequently, many times a day, I certainly don't want to have to type anything more than the file name before storing it.  I'd like to be able to store a file, as a web page or word-processing file (or whatever it might be), in the data location directly but on that separate hdd.  That's why I want my one home directory to be on that separate data hdd.

---

