---
title: "I'm looking for a security way to uninstall a python version. Somebody can help ??"
date: 2015-03-02
forum: Installation &amp; Upgrades
---

### Post by fbio7 on 2015-03-02
Hi everbody

I'm using ubuntu 14.04 LTS and recently I install a IDLE who change my python version. I saw in the internet some tips and I discovered the directory /usr/bin. It have all version of python install in my computer.

For my surprise in this directory there two verions of the python now...2.7.6 an 3.4.0...
Can I unistall a version of python without damage my ubuntu system. I saw in the internet that some guys unistall python with the comand remove and after that there are so many problems with the system.

If It&#347; dangerous unistall the version 2 or 3. Can I change a version default ?? So when I put in the terminal python3 to run a version3 and if necessary when put python2 to run the version2. 

I access diferent version using the comand line in ther terminal: /usr/bin/python3 (run version 3.4.0) and python (run version 2.7.6)

ps: (sorry for mistakes in the write my english is not the best)

---

### Post by oldfred on 2015-03-03
Do not uninstall either of the default installs of python. 
Ubuntu is in the process of converting from 2 to 3 and soon will be python3 as default but python2 will still be in repository.
But many scripts in Ubuntu require python.

As you mention python link is to python2 so running python defaults to 2.
If you want 3 just use python3

---

### Post by fbio7 on 2015-03-03
Hi oldfred...

I understood that ubuntu depends of python and unistall a wrong file maybe damage the system...so I will maintain the two versions. 

do you know how I change the link to execute python3 in terminal ??? Today I write usr/bin/python3 in the terminal for execute the version 3.4.0..


thanks for the tips.

---

### Post by ian-weisser on 2015-03-03
> **fbio7 said:**
> do you know how I change the link to execute python3 in terminal ??? Today I write usr/bin/python3 in the terminal for execute the version 3.4.0..

You don't change anything. /usr/bin/python3 is the proper way to launch the Python 3 interpreter in a terminal.

See [https://www.python.org/dev/peps/pep-0394/](https://www.python.org/dev/peps/pep-0394/) :
> 
[LIST]
[*]             *python2*            will refer to some version of Python 2.x. 
[*]             *python3*            will refer to some version of Python 3.x. 
[*]      for the time being, all distributions      *       should      *      ensure that *            python*            refers to the same target as             python2 
[/LIST]


---

### Post by Impavidus on 2015-03-04
On the command line (but not on the first line (magic number) of a script) you can skip the /usr/bin/ bit. Just the command python3 will do.

I think (not really sure about this) that all Ubuntu components using python3 explicitly call python3, whereas components relying on python2 may simply call python as their devs didn't consider the possible existence of an incompatible python3. So making python point to python3 will break things relying on python2.

---

### Post by fbio7 on 2015-03-04
Hum..ok guys. nothing change.

Thank you very much for answer my questions...

---

