---
title: "Problems with the cammand Make..."
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by alffa on 2006-09-06
Before that at all I ask for an excuse them for my horrible English... But you are my hope, I tell them...

I am new in linux (ubuntu) and it does a little time I it installed, only that I can't connect to Internet and use the repository for install a new programs, so I had to download the file httpd-2.2.3.tar.gz for install Apache2 And execute the following commands :

```
$ gzip -d httpd-2.2.3.tar.gz
$ tar xvf httpd-2.2.3.tar
```

Everything was nice

```
$ CC="pgcc" CFLAGS="-O2" \
./configure --prefix=/sw/pkg/apache \
--enable-rewrite=shared \
--enable-speling=shared
```

Equal

When I comes to this command

```
$make
```

The computer shows me this

> bash: make: orden no encontrada
 

Something as that "I do not find" the command

can you helpme please 

Graces(Thanks) and regards!!

---

### Post by Crayoneater on 2006-09-06
you need to install make: 
sudo apt-get install make

or better yet, you could do:
sudo apt-get install build-essential

you will need the internet to do that though...but you could download the ubuntu packages from another computer and install them using dpkg:
sudo dpkg -i package_name.deb

so you could get the apache ubuntu package, and install it using dpkg. search for it here: [http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)

you will need to install all of it's dependencies that you don't already have.

---

### Post by taurus on 2006-09-06
Just so you know, build-essential is on the CD so even if you don't have network connection, you still can use aptitude to install it.  Open a terminal and do

```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

```

---

### Post by alffa on 2006-09-06
thanks Crayoneater :

I did what you say to me and answers the following thing to me:

> The package make does not have candidate for its installation

what do you think about this ??

Thanks !!

---

### Post by alffa on 2006-09-06
Gracias taurus...

I am going to try with your option 

thanks again!

Greetings:D

---

### Post by alffa on 2006-09-06
pardon to respond so slow? but my English is very bad?

Gracias to both :-D :-D

---

### Post by taurus on 2006-09-06
After you unpack httpd-2.2.3.tar, you need to change to the new directory where the source is...

```

cd httpd-2.2.3
./configure
make
sudo make checkinstall

```

---

### Post by alffa on 2006-09-06
thanks taurus ... i will tray.

---

### Post by alffa on 2006-09-06
p.d. do you understand well what I write? 

or I am really very bad writing English?

---

### Post by taurus on 2006-09-06
> **alffa said:**
> p.d. do you understand well what I write? 

or I am really very bad writing English?
I understand you just fine.  ;)

---

### Post by alffa on 2006-09-09
Hola friends..

```
CC="pgcc" CFLAGS="-O2" \
./configure --prefix=/sw/pkg/apache \
--enable-rewrite=shared \
--enable-speling=shared
```


And it returns this mistake:

> .
.
.
checking for working mkdir -p... yes
APR Version: 1.2.7
checking for chosen layout... apr
checking for gcc... pgcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr

On the other hand..

Do you know some way of download a package with everything and dependences of an alone time without them having to go down one for one...

It is to say if I go where Crayoneate says to me I have that download each of the dependent packages (I create every red button) and this way up to ending with the whole directory ... is not it like that?

For this my previous question..

Thank you...

---

### Post by taurus on 2006-09-09
Do you know that httpd is available in the repos???

```

sudo aptitude update
sudo aptitude install httpd

```

---

### Post by alffa on 2006-09-09
well ... in Synaptic i look for Apache2 y it show my this ..

in package : apache2
in last version : 2.0.55-4ubuntu2.1

To this do you refer?

did you remember that i can't connect to internet ??

thanks ..

---

### Post by taurus on 2006-09-09
Yes, use synaptic to install it!  Why make it harder then it should be when a binary is available for you with a click on a mouse UNLESS you want to run the latest version...

---

### Post by alffa on 2006-09-09
what do you think if i delete from synaptic that version and i continue install with make ... because i can't connect to internet ??

saludos !!

---

### Post by taurus on 2006-09-09
Wait a second!  If you can't connect to the internet, then why do you want to run httpd/apache?  It doesn't make sense because httpd/apache is a web server and you need to be on the net to run any server...

---

### Post by alffa on 2006-09-09
Because this one computer it is in an intranet ... it is to say ... I need a server to give host service to a net computers ... but out of Internet...

Do I explain??

---

