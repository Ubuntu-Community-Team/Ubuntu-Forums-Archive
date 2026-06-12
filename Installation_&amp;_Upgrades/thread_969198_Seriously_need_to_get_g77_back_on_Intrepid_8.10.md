---
title: "Seriously need to get g77 back on Intrepid 8.10"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by kimmyjo74 on 2008-11-03
I just upgraded to Intrepid 8.10 this morning and was horrified to find out that g77 is no longer supported. I know that I can use gfortran to compile my own codes but I use some key software that requires g77 to compile job flows on the fly and without it I'm hooped. I am not able to hardwire this software to use gfortran. If I can't get g77 to work on Intrepid, I'm going to need to downgrade my Ubuntu. Help!!!

---

### Post by swhit on 2008-11-03
I agree. The developers really need to reconsider thier removal of g77 from ubuntu. Fortran 77 (g77) and Fortran 95 (gfortran) are not equivalent. 

This is exactly the reason why I left redhat/fedora for ubuntu. Fedora stopped including gnumeric and g77. Getting these two programs installed into Fedora was too much of a hassle compared to changing distributions.

Maybe it's time for me (and others like me) to abandon ubuntu. Does anyone know if OpenSuse supports g77?

---

### Post by whazooo on 2008-11-03
this seems to be fixed in gcc-3.4 (3.4.6-8ubuntu2) intrepid

see this thread:

[https://bugs.launchpad.net/ubuntu/+source/gcc-3.4/+bug/249991](https://bugs.launchpad.net/ubuntu/+source/gcc-3.4/+bug/249991)

---

### Post by ad_267 on 2008-11-03
They included the libg2c library needed to run code compiled with g77, but I'm not sure if they included g77.

---

### Post by kimmyjo74 on 2008-11-04
I managed to get my software running again by compiling g77 from source. I'm happy now.

---

### Post by skorpio11 on 2008-11-04
Can you post how you accomplished this ...

Thanks

---

### Post by serexia on 2008-11-05
also, could you tell where did you get the source from?

@swhit: if you were serious, OpenSuse supports g77, but you don't wanna change to suse...

---

### Post by swhit on 2008-11-05
> **serexia said:**
> also, could you tell where did you get the source from?

@swhit: if you were serious, OpenSuse supports g77, but you don't wanna change to suse...

I'm also very interested in the steps used for compiling g77 on ubuntu 8.10.

As for switching to OpenSuse, yes, I'm serious. Right now, I'm waiting until the next version of OpenSuse is released (which I think is scheduled for December). When it's released, I will give it a try. If installation of OpenSuse goes smoothly, and g77, gnumeric, and pymol are present (the less mainstream programs I use heavily), then I will become an OpenSuse user. Nothing against Ubuntu. I just prefer an easy to install OS that runs the programs I use, and gets updated regularly (the linux desktop world evolves quickly). 

If compiling g77 is easy on ubuntu, then I have no need to switch distributions. I've compiled custom versions of gnuplot in the past when readline support was removed. But, I've heard that g77 is much more difficult to compile.

---

### Post by jimv on 2008-11-05
Why not just go download the DEB from the Hardy repo?

[http://packages.ubuntu.com/hardy/g77-3.4](http://packages.ubuntu.com/hardy/g77-3.4)

---

### Post by Budoc on 2008-11-05
I find myself in a similar predicament to the poster of this thread. I've been given a file to compile that is written in fortran77. I've tried to use gfortran and fort77 without success. The file that I need to compile has previously been compiled successfully with a Windows-based fortran 77 compiler. I'd at least like the opportunity to attempt to compile it using g77 to see whether I can compile and execute the file without having to leave my beloved ubuntu environment.


> **jimv said:**
> Why not just go download the DEB from the Hardy repo?

[http://packages.ubuntu.com/hardy/g77-3.4](http://packages.ubuntu.com/hardy/g77-3.4)

Despite having gcc-3.4 installed, in the package installer window I get "Error: Dependency is not satisfiable: gcc-3.4" as the status.

---

### Post by swhit on 2008-11-06
> **jimv said:**
> Why not just go download the DEB from the Hardy repo?

[http://packages.ubuntu.com/hardy/g77-3.4](http://packages.ubuntu.com/hardy/g77-3.4)

I've tried this; doesn't install. A laundry list of dependencies occur, which can be fixed by searching out and installing the correct libraries. Upon doing this, however, subsequent 8.10 updates were not compatible (i.e., the 8.10 updates promptly removed the g77 installation).

---

### Post by horvathd on 2008-11-09
I solved this problem with adding the hardy's univese repositories to my source.list. This way I could install g77 with aptitude, while gcc was downgraded to 3.4.6-6, but now it's working.

---

### Post by MMonty1960 on 2008-11-11
I tried to add the hardy's universe repositories, but I did not find the g77 package. I initially attempt to operate on the synaptics GUI and later directly on the file source.list, but g77 remains unavailable. Could you tell me exactly the steps you followed?

---

### Post by horvathd on 2008-11-12
I just added the following lines to the source.list after the lines of universe repositories for intrepid:

```
deb http://hu.archive.ubuntu.com/ubuntu/ hardy universe 
deb-src http://hu.archive.ubuntu.com/ubuntu/ hardy universe 
deb http://hu.archive.ubuntu.com/ubuntu/ hardy-updates universe 
deb-src http://hu.archive.ubuntu.com/ubuntu/ hardy-updates universe
```

(Note: *hu* should be changed to your country code i.e. *us*, *gb*, *de*, etc.)

after that in the terminal:

```
sudo aptitude update
sudo aptitude install g77
```

That worked for me.

---

### Post by mikiman95 on 2008-11-14
I've got the same problem... Altough gfortran 'seems' to compile programs right, I think it's just a matter of time to check for incompatibilities.

So, my question is: are they going to put it back into Ubuntu?? If the answer were 'no', it would be my first really serious problem with Ubuntu... and I don't want that happens!

---

### Post by VOLKOV9 on 2008-11-15
I've got the same problem: I have code that worked in g77 and doesn't with fort77, f2c, and/or gfortran.

Following the instructions above (adding the repos and using apt-get) did not work because of a dependency issue with g77-4.3.

Someone earlier mentioned compiling g77 from source, but I can't find how to do that - Does anyone know how that works?

Thanks.

PS: Do we know why they got rid of g77?

---

### Post by pauljoseph on 2008-11-17
I tried to add Hardy repository, and do sudo apt-get install g77, but I got this error:

```
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
Some packages could not be installed. This may mean that you have               
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  g77: Depends: g77-3.4 (>= 3.4.6-1) but it is not going to be installed
E: Broken packages

```

please advise, I need g77 for my work.

---

### Post by horvathd on 2008-11-17
Dear All,

I tried to reproduce the steps I made to install g77. I followed the instructions I wrote above, and I also got the error messages you posted.

Then I tried to install with aptitude, and it made possible to install g77 whit downgrading gcc, and some other components.

Sorry for the inconvenience.

(I also updated my post above.)

---

### Post by mikiman95 on 2008-11-18
I did the steps in the post with aptitude, and it worked.

What was amazing for me was the fact that I reached to compile with gfortran my fortran code changing some ideas in the scripts I used to have to manage the compilation. But the numerical results I got were different compiling with g77 and gfortran. Of course, this can be just an error of my code -wich, on the other hand, used to work properly-, in the sense that some lines could be not very nicely written, and g77 interprets them in a different way than gfortran does.

---

### Post by sayantandas on 2008-12-04
> **horvathd said:**
> Dear All,

I tried to reproduce the steps I made to install g77. I followed the instructions I wrote above, and I also got the error messages you posted.

Then I tried to install with aptitude, and it made possible to install g77 whit downgrading gcc, and some other components.

Sorry for the inconvenience.

(I also updated my post above.)

hi horvathd ,

it would be very helpful if u cant tell us how and what changes u made to get g77 installed in intrepid.

thanx

---

### Post by horvathd on 2008-12-11
Hi sayantandas,

did you tried the steps I written in the post #14 in this topic?

---

### Post by zjuosu on 2008-12-18
> **horvathd said:**
> I just added the following lines to the source.list after the lines of universe repositories for intrepid:

```
deb http://hu.archive.ubuntu.com/ubuntu/ hardy universe 
deb-src http://hu.archive.ubuntu.com/ubuntu/ hardy universe 
deb http://hu.archive.ubuntu.com/ubuntu/ hardy-updates universe 
deb-src http://hu.archive.ubuntu.com/ubuntu/ hardy-updates universe
```

(Note: *hu* should be changed to your country code i.e. *us*, *gb*, *de*, etc.)

after that in the terminal:

```
sudo aptitude update
sudo aptitude install g77
```

That worked for me.

Thanks a lot. I got g77 installed following your instructions.
I got a new problem here.
How can I, as a Linux newbie, prevent g77 from being deleted by software updating service?

---

### Post by horvathd on 2008-12-19
Hi zjuosu!

Sorry, but I can't give the optimal solution because I use my linux only in command line mode.

I would do the following:
1.) Disable somehow the automatic update
2.) Periodically use the following command in a terminal:
```

sudo aptitude update
sudo aptitude safe-upgrade

```

---

### Post by zjuosu on 2008-12-20
Dear horvathd,
Thanks a lot.
It works.
I really appreciate your help.

---

### Post by santana on 2009-01-30
Still no answer as to why it was removed. Every one reading this thread should make noise because as much as people don't want to admit g77 still necessary part of life, and not having it in the ibex repo complicates our lives.

---

### Post by mwparis on 2009-02-06
> **horvathd said:**
> I solved this problem with adding the hardy's univese repositories to my source.list. This way I could install g77 with aptitude, while gcc was downgraded to 3.4.6-6, but now it's working.

Could you explain, at the idiot-level for me, how exactly you "add hardy's universe repositories" to the source.list?

I tried uncommenting the line "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse" (and then "sudo apt-get install g77") in /etc/apt/sources.list to no avail.

Muchas gracias.

---

### Post by mwparis on 2009-02-06
> **mwparis said:**
> Could you explain, at the idiot-level for me, how exactly you "add hardy's universe repositories" to the source.list?

I tried uncommenting the line "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse" (and then "sudo apt-get install g77") in /etc/apt/sources.list to no avail.

Muchas gracias.

Sorry. I see the solution in one of the posts above.

Thanks. I'll try it out.

---

### Post by Newtie on 2009-02-22
Hello,

I've also tried to get g77 back using the aptitude manager, by adding the hardy repositories to my sources list, updating aptitude & then trying to install g77. I can't seem to actually install it, however; aptitude only returns that there is no candidate version for g77 found to be available for install, then presents a long list of packages it asks for permission to remove, which I don't feel comfortable doing.

Does this mean you can no longer get g77 from the hardy repositories also? 

Is there any other way to get g77 on Ubuntu 8.10?

---

### Post by bmcage on 2009-03-09
People, please see: 
[http://gcc.gnu.org/onlinedocs/gcc-3.4.6/g77/News.html#News](http://gcc.gnu.org/onlinedocs/gcc-3.4.6/g77/News.html#News) 

They say: 
> GCC 3.4.x is the last edition of GCC to contain g77 - from GCC 4.0 onwards, use gfortran

So move to gfortran now.

---

### Post by atish on 2009-03-19
> **horvathd said:**
> I just added the following lines to the source.list after the lines of universe repositories for intrepid:

```
deb http://hu.archive.ubuntu.com/ubuntu/ hardy universe 
deb-src http://hu.archive.ubuntu.com/ubuntu/ hardy universe 
deb http://hu.archive.ubuntu.com/ubuntu/ hardy-updates universe 
deb-src http://hu.archive.ubuntu.com/ubuntu/ hardy-updates universe
```

(Note: *hu* should be changed to your country code i.e. *us*, *gb*, *de*, etc.)

after that in the terminal:

```
sudo aptitude update
sudo aptitude install g77
```

That worked for me.

It works ! Thanks !

---

### Post by UWCIVIL on 2009-04-07
Thanks so much for this very clear post.  It worked for me.  The only thing that a new user like me could have used was the the sources.list file can be found in /etc/apt/

Thanks again


> **horvathd said:**
> I just added the following lines to the source.list after the lines of universe repositories for intrepid:

```
deb http://hu.archive.ubuntu.com/ubuntu/ hardy universe 
deb-src http://hu.archive.ubuntu.com/ubuntu/ hardy universe 
deb http://hu.archive.ubuntu.com/ubuntu/ hardy-updates universe 
deb-src http://hu.archive.ubuntu.com/ubuntu/ hardy-updates universe
```

(Note: *hu* should be changed to your country code i.e. *us*, *gb*, *de*, etc.)

after that in the terminal:

```
sudo aptitude update
sudo aptitude install g77
```

That worked for me.

---

### Post by chamithmalinda on 2009-10-05
Please go to this link......... n help me [COLOR=Red]same problem[/COLOR] here.........

[http://ubuntuforums.org/showthread.php?p=8057446#post8057446](http://ubuntuforums.org/showthread.php?p=8057446#post8057446)

---

### Post by sreekarguddeti on 2009-10-09
@horvath
thanks for the clear howto
i owe you one

sreekar
india

---

