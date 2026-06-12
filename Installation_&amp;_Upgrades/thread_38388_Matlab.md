---
title: "Matlab"
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by [pl]ice on 2005-05-31
hi, 
  i have installed matlab; problem :
      i can only run it from shell:
 /usr/local/bin/matlab
Inconsistency detected by ld.so: rtld.c: 1259: dl_main: Assertion `_rtld_local._dl_rtld_map.l_prev->l_next == _rtld_local._dl_rtld_map.l_next' failed!

i get that. I searched on ubuntu for this, and the solution didn' t work from one of the posts. Anyway, matlab still runs , but i can't run it from my start menu. I have done:
  edit menu, add link, and for execute i have put /usr/local/bin/matlab
             the pop up Matlab 7 shows up, then just cancels itself.

i don't know what's wrong.
thanks.

---

### Post by ubuntme on 2005-08-30
yeah, matlab linux is pretty dodgy.

A work around for you, to run matlab from a menu use:
xterm -e matlab

replace xterm with whatever terminal program you use.

personally, I think the GUI sucks, (R13).  I run xterm -e matlab -nosplash -nodesktop to start matlab as command line only... or xterm -e matlab -nojvm to start matlab without starting the slow JVM.

Hope this helps

---

### Post by [pl]ice on 2005-08-30
thanks man, sorry i lost that post :]

 i found why it's crashing, well the reason.. ;  it doesn't like when you start copy/paste from matlab!! shocker.

---

### Post by ubuntme on 2005-08-30
I assume the problem is something to do with the JVM, or it is know that Klipper has problems with matlab (if you use KDE), have you looked in the mathworks forums?

[http://www.mathworks.com/matlabcentral/](http://www.mathworks.com/matlabcentral/) 

take a look through the newsgroups...

Does it still crash if you start without JVM?

Also I just found out if you run matlab using xterm -e nohup matlab & it closes the xterm straight after matlab opens so that you don't have an extra teminal lying around...  :)

---

### Post by dannemil on 2005-08-30
[QUOTE=ubuntme]I assume the problem is something to do with the JVM, or it is know that Klipper has problems with matlab (if you use KDE), have you looked in the mathworks forums?

[http://www.mathworks.com/matlabcentral/](http://www.mathworks.com/matlabcentral/) 

take a look through the newsgroups...

Does it still crash if you start without JVM?

Also I just found out if you run matlab using xterm -e nohup matlab & it closes the xterm straight after matlab opens so that you don't have an extra teminal lying around...  :)[/QUOTE]

Are you starting the license manager before you try to start matlab? To get it to run on my Ubuntu linux installation I use these commands in a terminal

cd /usr/local/matlab/etc
bash lmstart #this starts the licence manager
cd ../
cd bin
matlab

Maybe it's not starting from the menu because you have to start the lm first?

Good luck

---

### Post by chandra on 2005-09-01
To launch MATLAB from an icon, associate this command with the icon:

setsid /usr/local/bin/matlab -desktop

where you replace

/usr/local/bin/matlab

with the path to your executable.

I do not know if this will solve your specific problem, thoug

---

### Post by ubuntme on 2005-09-05
no, the problem is nothing to do with the licence manager or running from an icon.

Running from a terminal is fine, but for some reason running from a menu or an icon (same difference) is a pain.  It must be done form a terminal :(

This seems to be a well known problem with matlab based on my net research.

---

### Post by ubuntme on 2005-09-05
I should clarify that those commands I put up there are to be put into the exec bit of whatever menu, not from a command line where it is uneccesary.

---

### Post by [pl]ice on 2005-09-24
i've done that:
[http://www.ubuntuforums.org/showthread.php?t=40997&highlight=matlab](http://www.ubuntuforums.org/showthread.php?t=40997&highlight=matlab)

solved the lic6 problem,


ubuntme

can u explain more exactly where to put  xterm -e nohup matlab &
i got output :

nohup: do&#322;&#261;czanie wyników do `nohup.out'
(adding results to 'nohup.out')

 but now i'm caming out with:

matlab

----------------------------------------------------------------------------
Warning: glibc 2.2.0      - Unsupported version
         glibc -          - MATLAB built using this version
----------------------------------------------------------------------------
-> Your configuration APPEARS to be too OLD to run this MATLAB program!
----------------------------------------------------------------------------
   For system requirements consult [http://www.mathworks.com](http://www.mathworks.com) ...

***************************************************************************
-> Best to quit by pressing <return> at the next prompt ...

   Do you still want to try to continue? (y/[n]) >


it works, but is there a way to pass variable y  to matlab, 
eg. matlab <y   

it accepts 'y' in matlab, then quits :D

? so i don't have to keep yyyy  ;)

---

### Post by ubuntme on 2005-09-30
Not sure where you are with this,

But a better solution for the running matlab from a menu / icon comes from mathworks:
[]("http://www.mathworks.com/support/solutions/data/1-1B5ZV.html?solution=1-1B5ZV")

this is the same solution as chandra's above.

Basically when you create a menu or icon replace "/usr/local/matlab7/matlab" with "setsid /usr/local/matlab7/matlab -desktop" (change the path to whatever path you use...

not sure about the glibc thing, can you upgrade to a newer version? 

I haven't found any errors similar to yours on the web.... though there are many glibc and java errors in older versions of matlab...

---

### Post by [pl]ice on 2005-09-30
hm, i had error :
/lib/libc.so.6: Permission denied  after each startup of matlab, then i was stuk with console while using matlab,
by changing lines in couple of files, where it's asking about libc, solved that, but now i have to pass 'y' to maltab as it asks everytime, ur library is too old bla bla bal bla, continue? after y is ok
but i can't pass 'y' and using it from icon, couse it would simply wait for y upon execution. 
i'll try to re-install it :)

---

### Post by ubuntme on 2005-10-03
I think a reinstall may be worth a shot, next I would post your error on the mathworks forum... Or email mathworks support.

good luck

---

