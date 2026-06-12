---
title: "bash error with Gnu Radio 3.6.3"
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by seacher1 on 2013-05-19
While editing the PYTHONPATH after restart I get the following response.

bash: /usr/local/lib/pkgconfig:/usr/local/lib/python2.7/dist-packages:/usr/lib/python2.7/dist-packages:/home/gnuradio-3.6.3/uhd/host/build:: No such file or directory

Has anyone experienced a similar issue or can direct me to something that can help.  I have searched for three days now and have found similar issues but no solutions.

Thanks for your reply and help in advance.

---

### Post by steeldriver on 2013-05-19
Hello and welcome to the forum

Where and how did you edit the PYTHONPATH variable? it sounds like you have a syntax error that is causing the shell to try to interpret the path as a command

---

### Post by seacher on 2013-05-19
I edited the python path in the bash file.

Is this not the appropriate place?

---

### Post by seacher on 2013-05-19
Also, I used the same syntax I used in a previous version of Ubuntu.

---

### Post by seacher1 on 2013-05-20
I have deleted all the edited lines from my bash file and get this message now when invoking the benchmark code:

Traceback (most recent call last):
  File "benchmark_rx2.6a.py", line 23, in <module>
    from gnuradio import gr, gru, modulation_utils
Import error: cannot import name modulation_utils

One problem is resolved, but another seems to have risen.

I am relatively new to linux and gnu radio, but really want to be able to understand them both.

I will keep working on my end, but could really use some help from more experienced users.

---

### Post by steeldriver on 2013-05-20
So did you manage to get your PYTHONPATH variable assigned correctly? the modulation_utils.py file comes from gnuradio, for example I have an older src tree on this machine, and it says

```
steeldriver@lap-t61p:~/src/gnuradio-3.2.2$ find . -name 'modulation*'
./gnuradio-core/src/python/gnuradio/**modulation_utils.py**

```

When you successfully install gnuradio from source, it probably puts the file somewhere like 

```
/usr/local/lib/python2.7/site-packages/
```

Then you would likely need to set PYTHONPATH e.g. to set it locally in the shell where you're running the benchmarks

```
export PYTHONPATH=/usr/local/lib/python2.7/site-packages
```

If the benchmark code runs OK after that, *then* you can worry about how to set PYTHONPATH persistently via your .bashrc file

---

### Post by seacher1 on 2013-05-20
I have not been able to set my PYTHONPATH yet. I used the export command then attempted to run my benchmark code and got the same print out about modulation_utils.

When I find my modulation_utils I get 6 results with .py, .pyc, .pyo, and just plain modulation_utils.

Plus, I get modualtion_blk.rst.

---

### Post by seacher1 on 2013-05-21
I have attempted to use these two sites as a reference to export my PYTHONPATH and neither one has worked.

[http://lists.gnu.org/archive/html/discuss-gnuradio/2013-01/msg00175.html](http://lists.gnu.org/archive/html/discuss-gnuradio/2013-01/msg00175.html)
[http://www.stereoplex.com/blog/understanding-imports-and-pythonpath\](http://www.stereoplex.com/blog/understanding-imports-and-pythonpath\)

Can someone direct me to a website that will help better than these two have?

---

