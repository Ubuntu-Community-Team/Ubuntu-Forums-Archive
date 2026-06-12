---
title: "I Goofed upgrade issues"
date: 2013-05-26
forum: Installation &amp; Upgrades
---

### Post by oldstumpy on 2013-05-26
Hi: All,I upgraded from ubuntu 11.10 to 12.04 tonight,my invoicing program was on my desktop i might add that it was a third party program so after upgrade it was gone can i get that program back some how or is gone forever? Thanks For any assistants oldstumpy PS. i was operating it in gnome 2d classic mode

---

### Post by sudo san on 2013-05-27
How did you upgrade?
Did you upgrade by booting from the 12.04 CD and select upgrade?
If yes, then yes, it has gone.
But if you used the upgrade manager while in 11.10, it should still be there. Search for it in the dash and it should be there.

If you installed it through ppa, you will need to edit the ppa file. Navigate to the ppa file in the terminal (Ctrl + Alt + Del):
```
cd /etc/apt/sources.list.d/
ls
```

Then to edit the ppa (It should end in '.list'):
```
sudo gedit [name of the ppa file here ]
```

Change everything 'oneiric' to 'precise'.
Then save the file then close it.

Now try to update the program:
```
sudo apt-get update && sudo apt-get upgrade
```

When it finishes, you should have the up-to-date program for 12.04.



Hope this helps:smile:

---

### Post by fantab on 2013-05-27
> **sudo san said:**
> 
Change everything 'lucid' to 'precise'.
Then save the file then close it.


11.10 was 'Oneric' and not 'Lucid'. So OP should "change everyting 'Oneric' to 'Precise'.

---

### Post by sudo san on 2013-05-27
> **fantab said:**
> 11.10 was 'Oneric' and not 'Lucid'. So OP should "change everyting 'Oneric' to 'Precise'.

Oh, yeah. Sorry, I get mixed up with code-names sometimes.

I will edit the post.
Thanks! :D

---

### Post by oldstumpy on 2013-05-27
Hello everyone,ok here is what happened i upgraded from 11.10 oneric to 12.04 LTS through the update manager. the program that i lost or can't find is a third party called busybee invoicing now i found some of the files but i can't find all the finished invoices or i assume they would be called the database of this program when i click on the file busybee it's like starting from scratch like i just down loaded it off the internet agian,the folder that contained my invoices was in documents/my invoices when i upgraded all my files should not have been erased when i upgraded should they have? gee i realy need some help here.Thanks

---

### Post by sudo san on 2013-05-28
Did you not backup your files before upgrading?

---

### Post by oldstumpy on 2013-05-28
Nope

---

### Post by oldstumpy on 2013-05-28
Hi:Sudo San,I want to thank you for your help in trying to figer this issue out.I finally did i was logged in as guest and not logged in as adminastrator so everything on my desktop was not showing.oldstumpy:p

---

### Post by sudo san on 2013-05-29
Ah good. So everything is as it should be? You are very welcome. I also hope I can help in the future. :)

---

