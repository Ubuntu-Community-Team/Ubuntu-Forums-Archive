---
title: "Why does lucid don't use my swap partition?"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-28
and use so much memorey?and how can i fix it?

---

### Post by Peter09 on 2010-04-28
The question is - why should it use your swap partition. Getting data back from Swap is so much slower that getting it from RAM.
 
So Linux keeps as much in RAM as possible. When you load an application its loaded into RAM - if you then stop the app Linux keeps alot of the data it was using in RAM. Start the app again and it comes up much faster. Its only when you start running low on RAM that Linux will start clearing out old data.
 
The Swap partition is used when you have run out of RAM for active applications, then Linux takes chunks of RAM not being used at the moment and writes it to disk, when you need it again it writes a different bit of RAM to disk and reads the contents of Swap in needs back to RAM .... SLOW.
 
Normally, for a desktop especially, if you are using a lot of Swap space on a regular basis you have not enough RAM.

---

### Post by aviramof on 2010-04-28
Ok i can get this so the question now is why lucid use more then 700MB of ram as you can see for your self in the pictures i have attached and here are two more pictures with out compiz meaing i am using metactiy now so what is going here?

---

### Post by Peter09 on 2010-04-28
Hi,
its difficult to tell you exactly why, obviously its made more difficult because of the language barrier, some bits of the pictures are unclear to me. The short answer is it depends on what you are doing now and what you have been doing. 
 
Firefox for instance uses a lot of RAM, perhaps having a lot of tabs (sites/pages) open increases usage. 
 
Also some libraries (code /data) can get loaded by default because you often use it (preloaded).
 
If you have been using large images, videos or data files, these can hang around in RAM.
 
Simplistically, if your system is performing OK and not giving you problems then your RAM usage is nothing to worry about. My experience is that Ubuntu needs about 512MB of RAM to run a desktop without touching the swapfile much. Heavy usage results in swapping.
 
So your usage is about right.

---

### Post by aviramof on 2010-04-28
i don't think that it should be so high with just one tab in Firefox and nothing else running what you see in the processes picture is everything can you add the numbers to 700MB?
and i just reinstalled ubuntu like two days ago what could possibly i have done that would make it use this much memory?

---

### Post by wojox on 2010-04-28
Did you change the vm.swappiness value?

---

### Post by Peter09 on 2010-04-28
Thats just your active tasks usage of memory, remember that some memory is occupied by data/code used by tasks that are not running now, or if preload is used then also data/code that is expected to be used in the future.
 
Run htop from a terminal, it will give you a better picture of memory because it shows 'active' usage, 'cached' usage etc.
 
You may need to install it from the repositories.

---

### Post by aviramof on 2010-04-28
> **wojox said:**
> Did you change the vm.swappiness value?

i don't even know how to do that not here in linux any way:)

i have attached an Htop picutre

---

### Post by Peter09 on 2010-04-28
You are using 630Mb of memory total ( the green segment is the percentage of that allocated to active tasks) the rest is cached memory etc.
 
Thats just about right.

---

### Post by aviramof on 2010-04-28
it's pretty much the same as my windows 7 but i remember it was much smaller maybe the fglrx driver have something 
to do with it but compare to what i have running here now  which is nothing it's pretty high.

and that without compiz.

i think it would have been better with kernel 2.6.33 except that the current fglrx driver don't even let me install it properly today.

---

### Post by dino99 on 2010-04-28
a way to dig out: static services vs dynamic services

---

### Post by Peter09 on 2010-04-28
Well, looking at HTOP you seem to be activley using somewhere between 300MB and 400MB that looks good to me. The rest is just Linux spreading out because its has the room to do so.

---

### Post by dino99 on 2010-04-28
note that there is an issue with python not deallocating pointers when needed, so each apps using python swallow your ram till cancelled.

still waiting python team to fix it.

---

### Post by aviramof on 2010-04-28
here is a new attachment with compiz and after a few minutes of idle.

and why the forum make the picture so small?

---

### Post by Peter09 on 2010-04-28
Why do you expect much difference, as allready discussed Linux is not going to reduce its total memory footprint much just because you are doing nothing. 
 
You still have about 400MB actively used, that includes your applications and all the applications associated with the operating system --- memory management, graphics, disk, security, network etc. I think thats impressive.

---

### Post by aviramof on 2010-04-28
When i used 2.6.33 kernel it was in the region of 200MB now it can reach 800MB so something here is very wrong.

Update: 
i have added a new picture after restart picture #7 and everything is fine so for what ever reason ubuntu don't release the memory as he should.

it could be the python problem or anything else but it's clear that it's not good.

---

### Post by aviramof on 2010-04-28
here is one more picture that would clarify how it should be all the time and not reach 800MB for no apparent reason and i didn't even closed transmission.

---

