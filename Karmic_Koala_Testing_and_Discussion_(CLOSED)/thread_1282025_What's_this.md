---
title: "What's this?"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 2roombas on 2009-10-03
A few seconds ago I tried a Synaptic Package Manager update on the 9.10 BETA and got this message after trying to apply....  Why?  Is it fixable?

[INDENT]W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libgomp1_4.4.1-4ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libgomp1_4.4.1-4ubuntu6_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/gcc-4.4-base_4.4.1-4ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/gcc-4.4-base_4.4.1-4ubuntu6_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libstdc++6_4.4.1-4ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libstdc++6_4.4.1-4ubuntu6_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/cpp-4.4_4.4.1-4ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/cpp-4.4_4.4.1-4ubuntu6_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/gcc-4.4_4.4.1-4ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/gcc-4.4_4.4.1-4ubuntu6_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libgcc1_4.4.1-4ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libgcc1_4.4.1-4ubuntu6_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.3.1+1403-0ubuntu25_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.3.1+1403-0ubuntu25_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.3.1+1403-0ubuntu25_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.3.1+1403-0ubuntu25_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.3.1+1403-0ubuntu25_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.3.1+1403-0ubuntu25_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.3.1+1403-0ubuntu25_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.3.1+1403-0ubuntu25_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/python-stdlib-extensions/python-gdbm_2.6.3-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python-stdlib-extensions/python-gdbm_2.6.3-0ubuntu1_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/python-stdlib-extensions/python-tk_2.6.3-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python-stdlib-extensions/python-tk_2.6.3-0ubuntu1_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xsplash/ubuntu-xsplash-artwork_0.8.2-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xsplash/ubuntu-xsplash-artwork_0.8.2-0ubuntu2_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xsplash/xsplash_0.8.2-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xsplash/xsplash_0.8.2-0ubuntu2_i386.deb)
  404  Not Found [IP: 91.189.88.31 80][/INDENT]

---

### Post by Thetherumcompound on 2009-10-03
I get a similar response when my computer is not connected to the internet or if i have the wrong proxy settings. Are you sure your connected to the internet?

---

### Post by 2roombas on 2009-10-03
> **Thetherumcompound said:**
> I get a similar response when my computer is not connected to the internet or if i have the wrong proxy settings. Are you sure your connected to the internet?

Well, I must be connected to the internet if I'm able to send this., no?  I'm actually using that computer right now.

---

### Post by Thetherumcompound on 2009-10-03
Very true!
Are you using a network with proxy settings? Mozilla Firefox(or whatever browser you are using) may have one set of proxy settings but the rest of the system may have another.

---

### Post by Lunx on 2009-10-03
Dunno if this'll help, but what happens if you switch repositories and try a different software source? Same problem's happen to me a few times in past and this has worked for me.

---

### Post by Lunx on 2009-10-03
You could also try upgrading by hitting Alt+F2 and typing 

```

update-manager -d

```

That's the way I upgraded a couple of days ago and all worked a treat for me, very smooth process.

---

### Post by tsger on 2009-10-03
> **Lunx said:**
> Dunno if this'll help, but what happens if you switch repositories and try a different software source? Same problem's happen to me a few times in past and this has worked for me.

Same here.  I usually choose the fastest server, but for some reason yesterday I had to change to the default Ubuntu server becasue I was getting errors similar to yours.

---

### Post by Lunx on 2009-10-03
Errr.... sorry. Re-read your post and see you already are using 9.10, whoops. :oops:

---

### Post by Mutt77 on 2009-10-03
Update manager is overwhelmed with everyone trying to get the beta. It keeps (nearly) crashing. Be patient it took me two days to finally get 9.10 fully upgraded.

---

### Post by Lunx on 2009-10-03
> **tsger said:**
> Same here.  I usually choose the fastest server, but for some reason yesterday I had to change to the default Ubuntu server becasue I was getting errors similar to yours.

I usually use the one mirror here as my ISP allows me to download stuff without it counting against my quota :)

Try doing that with Windows updates!!!

:)

---

### Post by 2roombas on 2009-10-03
I was able to update earlier this morning without problem,, and just now I switched from a "server in Canada" to the "main server" with the very same error. Odd?!

Oh, and by the way, Lunx, that id exactly how I upgraded last night.

---

### Post by 2roombas on 2009-10-03
> **Mutt77 said:**
> Update manager is overwhelmed with everyone trying to get the beta. It keeps (nearly) crashing. Be patient it took me two days to finally get 9.10 fully upgraded.

Aha... I had a feeling that might just be the the case!:P

---

### Post by Lunx on 2009-10-03
> **Mutt77 said:**
> Update manager is overwhelmed with everyone trying to get the beta. It keeps (nearly) crashing. Be patient it took me two days to finally get 9.10 fully upgraded.

I just sussed out update manager myself and it's now running a partial upgrade. Currently downloading files and that's going smoothly, so I'll see in a few minutes whether installing gives any grief I guess :)

Hope nothing breaks, gotta get some important stuff done later today...

---

### Post by Lunx on 2009-10-03
Hmmm, update failed halfway through downloading files. I'll try a bit later to complete downloading :)

---

### Post by cariboo on 2009-10-03
I've been getting the same errors using different servers. Try again later, or try a different server.

It looks like the load on the servers is finally starting to let up a bit.

---

### Post by 2roombas on 2009-10-03
I guess patience was all that I needed.  Iy just now updated without error!:)

---

### Post by FuturePilot on 2009-10-03
I got the same thing just now. It went away after a few minutes. Not sure what that's all about though.

---

### Post by DougieFresh4U on 2009-10-04
> **Lunx said:**
> I just sussed out update manager myself and it's now running a partial upgrade. Currently downloading files and that's going smoothly, so I'll see in a few minutes whether installing gives any grief I guess :)

Hope nothing breaks, gotta get some important stuff done later today...
You said 'partial upgrade', well you know what happens when 'partial upgrade' is allowed, your next post......

> **Lunx said:**
> Hmmm, update failed halfway through downloading files. I'll try a bit later to complete downloading :)

There have been so many questions regarding 'partial upgrades', when ever I see one, I abort and run like h@ll!

---

### Post by Lunx on 2009-10-04
> **DougieFresh4U said:**
> You said 'partial upgrade', well you know what happens when 'partial upgrade' is allowed, your next post......



There have been so many questions regarding 'partial upgrades', when ever I see one, I abort and run like h@ll!


Duly noted and thank you :)

I came across other things on this issue, and read the sticky, decided I won't be going down that path after all (thank god the server broke before it all downloaded!!!)

Everything working fine for me ATM, so might be a little more patient and wait 'til everything is sorted in a few weeks. Might even treat myself to a fresh install, why not , what's forty minutes + a little bit of other stuff?

:)

---

### Post by wnelson on 2009-10-04
External servers are updated from master servers and it takes time and the file name is sent then the file. So sync'ing up with the main servers takes time.

---

