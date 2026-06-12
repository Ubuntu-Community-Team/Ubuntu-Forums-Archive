---
title: "How to install .run file"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by spydeyrch on 2010-04-18
Hey guys, quick question. It has been a long time since I have had to do this but I don't remember how to install/run a .run file. I went to the permissions tab under the properties and set it to "allow executing file as program" but after a few moments it says that I need to run it as a super user, meaning I need to run it via the terminal. I don't remember how to run the file/program to install it. HUGE brain fart! :confused: Thanks for your helps guys!

-Spydey :guitar:

---

### Post by quadproc on 2010-04-18
> **spydeyrch said:**
> Hey guys, quick question. It has been a long time since I have had to do this but I don't remember how to install/run a .run file.
The solution depends on what kind of a file your .run file is.  It is probably either a sh or a bash script.  To run one of these, use
```
sudo bash <name_of_.run_file>
```
If the script needs any arguments then you can put them after the file name.  Oftentimes a script will offer a help argument, either -h or --help.  If your script is written in sh then substitute _sh_ for _bash_, above.

quadproc

---

### Post by spydeyrch on 2010-04-18
Awesome. Thanks for the help. I will give it a quick try. Once I read your post, it all came back to me. I have been working with windoze a lot lately and had a huge brain fart. Thanks for the refresher. :)

-Spydey:guitar:

---

### Post by quadproc on 2010-04-19
> **spydeyrch said:**
> Awesome. Thanks for the help. I will give it a quick try. Once I read your post, it all came back to me. I have been working with windoze a lot lately and had a huge brain fart. Thanks for the refresher. :)
You are welcome.  I am glad that I don't have to venture into the swamp myself.
If you haven't already, would you please mark this thread as solved?  Thanks.

quadproc

---

