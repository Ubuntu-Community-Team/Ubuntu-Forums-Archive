---
title: "Expect PHP extension trouble"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by onionbagle on 2007-08-28
Hi,

I am having trouble installing expect for PHP.  I downloaded the extension from here.
[http://pecl.php.net/package/expect](http://pecl.php.net/package/expect)

I then ran 'pear install expect-0.2.2.tgz'.  Then I got the error below.
configure: error: expect extension requires libexpect version >= 5.43.0
ERROR: `/tmp/tmpZesEHF/expect-0.2.2/configure' failed

I guess I need to install libexpect? I searched aptitude for it and found nothing.  I would really appreciate any help at all

Thanks

---

### Post by Pumalite on 2007-08-28
Do you have 'build-essential'? If not:
sudo apt get install build-essential

---

### Post by onionbagle on 2007-08-28
Hi Pumalite,

Thanks for your response. Well I installed build-essential and then ran 'pear install expect-0.2.2.tgz'.  I still got the same error message.   

configure: error: expect extension requires libexpect version >= 5.43.0

I haven't found much on installing libexpect or what other packages include it.  Any other suggestions?

Thanks

---

### Post by Pumalite on 2007-08-28
Do you have libexpect? If not: Synaptic>Search>libexpect>Install

---

### Post by onionbagle on 2007-08-28
Unfortunately I am at home now with only command line access.  I tried installing the vnc server with apt-get install vnc-common.  It was already installed but I couldn't find the program to make it run.  Just for future reference I am running 6.06 server edition if it makes a difference. I guess I will try searching for it when I get to my office and have the synaptic GUI.

---

### Post by Pumalite on 2007-08-28
Try sudo apt-get install libexpect

---

### Post by onionbagle on 2007-08-29
No luck with 'sudo apt-get install libexpect' either.  I even tried adding the universe repository to my sources.list file and then running 'sudo aptitude update'.  The only thing that seems to show up is libexpect-perl.  I haven't installed it because I thinks its just a perl module.

---

### Post by Pumalite on 2007-08-29
I think is more than a perl module.

---

### Post by onionbagle on 2007-08-29
Well I installed libexpect-perl.  Then I ran 'pear install expect-0.2.2.tgz' stil got the same error.
configure: error: expect extension requires libexpect version >= 5.43.0

I just checked my expect version with '/usr/bin/expect -v'  It looks like I have 5.42.1 which explains the error above.  I downloaded expect-5.43 from here expect.nist.gov/#unix  I unzipped it and ran the first ./configure and it says it can't find tcl.  I know I have tcl installed because I did a 'sudo apt-get install tcl8.0.  I also have tclsh tclsh8.0 tclsh8.3 and tclsh8.4 in /usr/bin.  I guess the ./configure is looking in the wrong place? so I made a link from /usr/local/src  named tcl and pointed it to /usr/bin/tclsh8.0.  That didn't work.  Here is the error I get from running ./configure    
checking for Tcl configuration... configure: warning: Can't find Tcl configuration definitions

Any ideas where to look next?

---

### Post by billturner on 2007-08-29
try this

```
sudo apt-get install expect-dev
```

that looks like it has the libexpect you need

---

### Post by onionbagle on 2007-08-29
Hi billturner,

Well when I did apt-get install expect-dev I noticed >  Setting up expect-dev (5.42.1-1.2ubuntu1) ...

My problem is that the PHP extension needs expect 5.43 and all the apt-get packages seem to load 5.42.  I have gone to the expect website and downloaded 5.43 but I can't get past the first step of the install procedure because it says it cannot find tcl which I think I have if you reference the post above.

So my new issue is I need to install expect 5.43 but everything I try leads to errors with tcl. Specifically this. > checking for Tcl configuration... configure: warning: Can't find Tcl configuration definitions

Just to cover the basics I have tried ```
sudo apt-get install tcl8.0
sudo apt-get install tcl8.0-dev
sudo apt-get install tcl8.3
sudo apt-get install expect-tcl8.3
sudo apt-get install expect-tcl8.3-dev
```

---

### Post by billturner on 2007-08-30
Hmm, then I'm not sure what to suggest next. From some quick searching, you may need to specify the exact location for the tcl config script.

First, see if this file/script exists:

/usr/lib/tclConfig.sh

If so, add some parameters to the configure command line when setting up expect, similar to this:

```
./configure --with-tclconfig=/usr/lib/tclConfig.sh --with-tkconfig=/usr/lib/tclConfig.sh
```

And if tclConfig.sh isn't in that location, put in the correct location in each of those parameters.

Here's the Google search I did where I came across this: [http://www.google.com/search?q=%22configure%3A+warning%3A+Can%27t+find+Tcl+configuration+definitions%22](http://www.google.com/search?q=%22configure%3A+warning%3A+Can%27t+find+Tcl+configuration+definitions%22)

---

### Post by onionbagle on 2007-08-30
It worked!

Thanks so much for the help billturner.  Also thank you Pumalite for your input too.

Here are the final instructions on how to install expect 5.43 and how to install php expect extension. In case anyone else has the same trouble I did.

> Get the expect php extention here: [http://pecl.php.net/package/expect](http://pecl.php.net/package/expect)
Then you need expect 5.43 so download that here: [http://expect.nist.gov/#unix](http://expect.nist.gov/#unix)


Now the install.

```

sudo apt-get install tcl8.4-dev
tar xvfz expect.tar.gz

install expect:
sudo ./configure --with-tclconfig=/usr/lib/tcl8.4 --with-tclinclude=/usr/include/tcl8.4/tcl-private/generic
make
make install

install expect php extension:
sudo pear install expect-0.2.2.tgz

```

I have yet to actually test any expect code in PHP but so far everything has built and completed successfully.

---

### Post by Pumalite on 2007-08-30
You are welcome, but I think credit should go to billturner here period.

---

### Post by billturner on 2007-08-30
Awesome! Glad I could help.

---

