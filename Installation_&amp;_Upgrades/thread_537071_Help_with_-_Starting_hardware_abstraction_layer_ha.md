---
title: "Help with - Starting hardware abstraction layer hald"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by Jaydii on 2007-08-28
Hello people!

I'm really new at this, so I would appreciate it if helpers used " neewbie talk ". 

I acutually searched for this problem and found a few threads. But no one with a clear answer. 
When I boot ubuntu it stops when: Starting hardware abstraction layer hald.. 
And I'm a patient fellow, so I wait but that just results in reboots over and over.
I can't start it in a text based mode either, but I'm sure the installation went smooth.

In the past threads the solution ofter requires one to be in a terminal. 
How do I get there through windows? Because I can't when i boot it, perhaps I'm doing something wrong.  
And more importantly what do I do when I'm there?

Thanks!

---

### Post by charles woodward on 2007-08-29
I am experiencing problems with hald locking up the system.

As far as I can tell (I've run it from the command line with verbose mode set) it locks up when it tries to do something with the serial ports - but I'm not sure what.

To be honest I think this is going to get quite technical - so I won't bore you with it all at the moment.  However I am going to look on the `hald` website to see if there are any pointers.  

If I find anything usefull (that is fairly easy to explain) I will let you know.

---

### Post by charles woodward on 2007-08-30
The basic problem is that `hald` tells the desktop where everything is (such as the graphics cards, and all other devices).

So without hald up and running, you probably can't have a desktop.

Now I have hald working on 7.04 (current live release) where it is version 0.5.8.1, but in gutsy it doesn't work (version 0.5.9.1) - so I guess if you can try a different version it may well work.  However to do that you need to know about the command line and all the commands - which I don't think you are from what you say.  

You could try a different release of Ubuntu (I think 6.04 and 6.10 are still available) and then it may well work.

Sorry can't be more helpful than that.

---

### Post by Jaydii on 2007-08-30
No that's better than nothing, ill try that.
Thanks, I'll let you know how it works out. 

//Jay

---

