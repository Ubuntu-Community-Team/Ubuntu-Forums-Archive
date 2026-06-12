---
title: "trying to do an md5sum"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by swoll1980 on 2007-06-07
the file im trying to sum is on my desktop i just downloaded it. I'm using feisty. Can someone give me the command to do the md5sum? Please.

---

### Post by vigleik on 2007-06-07
md5sum

---

### Post by swoll1980 on 2007-06-07
tryed that one no luck

---

### Post by NeoLithium on 2007-06-07
That's the correct way though... hmm. What error messages do you get, or just does it do nothing?

---

### Post by swoll1980 on 2007-06-07
does nothing

---

### Post by NeoLithium on 2007-06-07
Open up a terminal, type
```

cd /Desktop

md5sum <filename>

```
Is the file an ISO?

---

### Post by swoll1980 on 2007-06-07
No such file or directory

---

### Post by swoll1980 on 2007-06-07
then i tried it with the <> symblals unexpected token new line

---

### Post by NeoLithium on 2007-06-07
you don't need to add the <> symbols, that was just so I could show you where to put the filename.

cd Desktop (my bad on the upper post)
and try
md5sum filename

---

### Post by swoll1980 on 2007-06-07
I tryed cd download_directory  Too upon the advice of doing linux md5sum

---

### Post by decoherence on 2007-06-07
in the terminal window type md5sum then a space, so it should look like (without the quotes)

"md5sum "

note the space on the end. very important. don't press return yet.

now drag the file from your desktop on to the terminal window. it should print out the full path to the file. NOW press return and you should get the md5sum for that file.

---

### Post by swoll1980 on 2007-06-07
without the <> it tells me unknown file or directory

---

### Post by swoll1980 on 2007-06-07
Tried md5sum (space) drag and drop, it brought up path i pressed enter it waited like ten seconds And prompted me" nolan@BIGMAN:~/Desktop$"

---

### Post by NeoLithium on 2007-06-07
What kind of file are you trying to md5sum?

---

### Post by swoll1980 on 2007-06-07
I have problems opening X-CD-Roast   to command "sudo X-CD-Roast" nothing happens

---

### Post by swoll1980 on 2007-06-07
ubuntu 6.06.1 iso

---

### Post by NeoLithium on 2007-06-07
Ok, where is the file saved in your directory? Desktop? /home/nolan?

---

### Post by swoll1980 on 2007-06-07
on my Desktop   /home/nolan/Desktop

---

### Post by confused57 on 2007-06-07
Make sure to cd to Desktop:
```
cd Desktop
```

then enter md5sum,press spacebar, type in the first couple of letters of the name of the iso, then press "Tab", it should complete the iso filename, then press enter...shouldn't take but 5-10 seconds to get your md5sum.

---

