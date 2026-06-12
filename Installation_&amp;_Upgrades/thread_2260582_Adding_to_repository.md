---
title: "Adding to repository"
date: 2015-01-13
forum: Installation &amp; Upgrades
---

### Post by rakesh343 on 2015-01-13
I've mistakenly deleted Canonical from my repository. How to add them back?

---

### Post by sudodus on 2015-01-13
The easiest way is to install Synaptic via the Software Center, and then use Synaptic to check which repositories are install and add those that you want. Click re-read to update the list of available packages etc.

---

### Post by rakesh343 on 2015-01-13
How to add addresses in the APT Line in the 'Software & Updates' Dialog Box? I want to added Canonical in "Other Software".

---

### Post by sudodus on 2015-01-13
Do you mean 'Canonical Partners'? - there is a box that you can tick in the previous window.

Or do you mean only 'Canonical'? - I don't know if there is such a repository.

Please tell me what you want - for example a program package that is included in the repository you want to use.

---

### Post by rakesh343 on 2015-01-13
I was talking about this:

Go to Software &Updates> Other Software> Add...
In the dialog box, APT Line address is asked.

I've typed: [HTML]deb http://archice.canonical.com/ubuntu trusty partner[/HTML]


This has started showing the canonical partners options that were mistakenly removed. Hope this is alright now???

---

### Post by Karlchen on 2015-01-13
Hello, rakesh343.

> I've mistakenly deleted Canonical from my repository. How to add them back?Please, open a terminal window. Execute the command ```
inxi -r
``` This will enumerate the names of all of your sources.list files and their content.
Post the complete screen output here, please.

I assume that in the main Ubuntu file /etc/apt/sources.list  the following line will be absent: ```
deb http://archive.canonical.com/ubuntu trusty partner
``` Note: the string *trusty* refers to Ubuntu 14.04. In case you use a different Ubuntu version, *trusty* will have to be replaced by the corresponding nickname, e.g. by *vivid* for Ubuntu 14.10.

In order to add this line back to the file  /etc/apt/sources.list, you will have to edit the file with root permissions. ```
sudo gedit /etc/apt/sources.list
``` Add the missing line as the last line and save the file.

HTH,
Karl
--
Oh, I see our posts almost crossed. Yep, your line looks all right.

---

### Post by rakesh343 on 2015-01-13
Thanks Karlchen,

It seems so. :-)

But still I got to learn something about the relatioship between the GUI and command line method. :-)

By the way, my system does not have 'inxi' installed. Should I?

---

### Post by sudodus on 2015-01-13
You can run synaptic and look at the windows for repositories. You will find  'Canonical Partners' - there is a box that you can tick in the previous window (and it should be ticked now, that you have that repository included in your setup.

It takes some time to get used to all these things and to identify the items behind the curtains (via command line tools) and the corresponding graphical interface. You are welcome to ask and discuss about such things whenever you need it in the future :-)

Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by rakesh343 on 2015-01-13
Thanks Karlchen for the support and encouragement. I'll certainly try to learn.
I'm marking it asSOLVED now. :-)

---

### Post by Karlchen on 2015-01-14
Hello, rakesh343.

Maybe inxi  does not come with Ubuntu 14.04 by default. But it can be got from the software repositories. As I found out how useful it can be whenever you want to get information about various aspects of your system, I added it to my Ubuntu 14.04.

Cheers,
Karl

---

