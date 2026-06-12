---
title: "php by default"
date: 2008-11-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mariuz on 2008-11-07
PHP ships with Mac OS X by default 

In ubuntu we should include php by default
i will submit an request or idea poll to be included

I spoted this over this page 
[http://www.phoronix-test-suite.com/?k=downloads](http://www.phoronix-test-suite.com/?k=downloads)

---

### Post by Quikee on 2008-11-07
But why? If OSX has PHP included it doesn't mean Ubuntu should also without any particular reason. Phoronix test suite is also not a real good reason as it is not even in Ubuntu's universe repository.

What reason is there to include PHP by default in your opinion? Which PHP applications in the repository (or not) are such that should be included by default into Ubuntu?  What advantages in your opinion should PHP have over for example Python as a choice of a programming language for desktop (and also web) applications which could potentially be included by default into Ubuntu?

---

### Post by Gina on 2008-11-07
I don't really see the need for including any programming language in the CD.  Anyone who wants to program should be competant enough to install from the repositories,  It's not rocket science and certainly easier than trawling the web for applications to install in certain other OSs.  But I like the idea of including everything most users want like browser, email, office suite and multimedia,

---

### Post by Naddiseo on 2008-11-07
> **Gina said:**
> I don't really see the need for including any programming language in the CD.  Anyone who wants to program should be competant enough to install from the repositories

There are python/perl programs that are installed by default, so they must be shipped with ubuntu.

Back to topic: There isn't much reason to include PHP, we have perl and python, and if you have php, you'll probably need apache to run webpages. And very few users will ever need apache/php.

---

### Post by danf_1979 on 2008-11-08
No need!

---

### Post by kernelhaxor on 2008-11-09
I don't see a need either .. I'm actually surprised OS X does it

---

### Post by ruik on 2008-11-10
Yeah, no need for PHP by default.

---

### Post by mariuz on 2008-11-13
it's about php-cli 
so php programmers could do scripts easier
than writing them in bash/perl/php or python 

Here are some examples of scripts that i have created to automate 
installation on new ubuntu server nodes

[http://github.com/mariuz/firebird_scripts/tree/master](http://github.com/mariuz/firebird_scripts/tree/master)

I wish php was there by default because almost all the scripts needs
to install php-cli first 

I posted an new idea to the brainstorm area

[http://brainstorm.ubuntu.com/idea/15590/](http://brainstorm.ubuntu.com/idea/15590/)

---

### Post by ccw on 2008-11-13
> **mariuz said:**
> it's about php-cli 
so php programmers could do scripts easier
than writing them in bash/perl/php or python 

Here are some examples of scripts that i have created to automate 
installation on new ubuntu server nodes

[http://github.com/mariuz/firebird_scripts/tree/master](http://github.com/mariuz/firebird_scripts/tree/master)

I wish php was there by default because almost all the scripts needs
to install php-cli first 

I posted an new idea to the brainstorm area

[http://brainstorm.ubuntu.com/idea/15590/](http://brainstorm.ubuntu.com/idea/15590/)

pass.

---

### Post by carlholmberg on 2008-11-13
My primary computer is a iMac G5 with Mac OS X 10.5 so I can see the pros with this along with Apache. At the same time it would add about 10 MB to the CD (I think).

Those who would need this are probably too few to actually merit adding this to the install CD (at the expense of other packages). I am also perfecly comfortable installing it after install...

---

### Post by Naddiseo on 2008-11-13
> **mariuz said:**
> it's about php-cli 
so php programmers could do scripts easier
than writing them in bash/perl/php or python 

Here are some examples of scripts that i have created to automate 
installation on new ubuntu server nodes

[http://github.com/mariuz/firebird_scripts/tree/master](http://github.com/mariuz/firebird_scripts/tree/master)

I wish php was there by default because almost all the scripts needs
to install php-cli first 

I posted an new idea to the brainstorm area

[http://brainstorm.ubuntu.com/idea/15590/](http://brainstorm.ubuntu.com/idea/15590/)

From what I can tell, all those scripts don't use much PHP, they're just passing commands to the shell. So, you don't /need/ PHP, you can just take those commands, and paste them into a shell file. Less typing too.

---

### Post by supernovus on 2008-11-14
We don't need PHP by default.

Most system scripts are written in Bourne Shell Script, Perl or Python. If you have scripts written in php, install php before running them :-)

I have scripts written in Perl 6, but that doesn't mean I think Rakudo or Pugs should be included by default (yet). Actually, Pugs was pulled from the repos entirely. Too bad really, as it's most useful feature was the ability to use Perl 5 modules in Perl 6 programs. However, I digress.

I have a list of common stuff I install on every system. If you need PHP, just add it when you first install. Easy!

---

