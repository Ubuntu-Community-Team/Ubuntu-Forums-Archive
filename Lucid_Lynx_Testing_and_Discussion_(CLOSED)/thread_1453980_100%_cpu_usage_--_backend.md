---
title: "100% cpu usage -- backend?"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by snowman63 on 2010-04-11
I have a Quad-core desktop and the same issue, Ther ia always one core at 100%, it varies every few minutes which. I do an update check several times a day to load any update but so far no joy. It does slow the system down sometimes. Any one else have this issue? I wouldn't this was solved at all.

---

### Post by snowman63 on 2010-04-11
I ran top and found that  backend is using 100% CPU if that helps. Here a view of it:

top - 17:13:45 up 1 day,  1:53,  2 users,  load average: 1.15, 1.18, 1.14
Tasks: 199 total,   2 running, 196 sleeping,   0 stopped,   1 zombie
Cpu(s): 22.9%us,  3.5%sy,  0.0%ni, 73.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8127176k total,  4391196k used,  3735980k free,   373072k buffers
Swap:        0k total,        0k used,        0k free,  2677348k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
10380 root      20   0 26948 6128 2460 R  100  0.1   1423:02 backend            
 1218 root      20   0  141m  47m  19m S    1  0.6  40:55.19 Xorg               
 2149 snowman   20   0  288m  56m  22m S    1  0.7  13:44.96 compiz             
30316 snowman   20   0 40348  30m 1276 S    1  0.4   0:19.53 script_ubuntu_1    
15047 snowman   20   0  211m  15m  10m S    1  0.2   0:00.72 gnome-terminal     
 2009 snowman   20   0  510m  43m  22m S    1  0.5  22:50.96 superkaramba       
 1850 root      20   0  453m 153m  11m S    0  1.9   1:07.12 java               
15341 snowman   20   0 19216 1476 1052 R    0  0.0   0:00.94 top                
    1 root      20   0 23676 1948 1268 S    0  0.0   0:00.83 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.08 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:06.26 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.05 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:11.92 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT   0     0    0    0 S    0  0.0   0:00.10 migration/2

---

### Post by mdance86 on 2010-04-14
I have the same problem.  Only I have a HP DM3 with AMD processor.  One of them is almost ALWAYS 100% which makes my battery run down fast, as well as create a very hot working environment.  I don't remember it being this way... under 9.10 it was faster and ran cooler than Windows 7 ever did.  Are the developers aware of this issue that seems to becoming popular?

---

### Post by WinterRain on 2010-04-14
> **mdance86 said:**
> Are the developers aware of this issue that seems to becoming popular?

They will be if you file a bug report. ;)

---

### Post by lavinog on 2010-04-14
Does anyone know what backend is?
can you post:
```

ps -eo pcpu,args|sort -rn|head

```

---

### Post by cariboo on 2010-04-14
There is a list of all the packages with the word backend in the name [here]("http://packages.ubuntu.com/search?keywords=backend&searchon=names&suite=lucid&section=all"). Take your pick.

---

### Post by uRock on 2010-04-14
install and use HTOP instead of TOP. HTOP gives you the ability to highlight and kill a process. It is a very handy terminal tool.

Cheers,
Ronnie

---

### Post by cariboo on 2010-04-14
You can do the same thing with top.

---

### Post by uRock on 2010-04-14
TOP doesn't show ya what to hit to make it happen. :)

---

### Post by cariboo on 2010-04-14
Run top and press h.

---

### Post by lavinog on 2010-04-14
htop is prettier.

Anyways, killing the process isn't the right fix for this...should we expect a user to do this everytime?
top doesn't show the full command of the process (that I know of)
There are plenty of processes that are called backend...(I am thinking cups would be a good suspect though)
finding the command line argument would be a nice clue.

---

### Post by Gorlist on 2010-04-14
I had this problem with my duel core laptop, 2nd core was running constantly at a 100% - but since updating 2 days ago seemed to clear up the problem. This PC (AMD Quad) hasn't had the problem.

---

### Post by uRock on 2010-04-14
> **lavinog said:**
> htop is prettier.

Anyways, killing the process isn't the right fix for this...should we expect a user to do this everytime?

Nope, Just a temp fix to cool the system, while the OP finds the real problem.

---

### Post by sdowney717 on 2010-04-14
I like system monitor. Lets you right click kill process etc...

---

### Post by uRock on 2010-04-14
> **sdowney717 said:**
> I like system monitor. Lets you right click kill process etc...

It doesn't show hidden processes though. It is definitely easier to read.

---

### Post by sdowney717 on 2010-04-14
[http://www.informit.com/articles/article.aspx?p=770644](http://www.informit.com/articles/article.aspx?p=770644)
according to this, it does show hidden processes.
But when i look for hidden in the menuing all I see is a selection for All processes
> $ gksudo gnome-system-monitor

From the Process Listing view (chosen via the tab in the upper-left portion of the window), select a process and click on More Info at the bottom left of the screen to display details on that process at the bottom of the display. You can select from three views to filter the display, available in the drop-down View list: All Processes, My Processes (those you alone own), or Active Processes (all processes that are active).

Choose Hidden Processes under the Edit command accessible from the top of the display to show any hidden processes (those that the kernel does not enable the normal monitoring tools to see). Select any process and kill it with End Process.

The processes can be reniced by selecting Edit, Change Priority. The View selection from the menu bar also provides a memory map. In the Resource Monitor tab, you can view a moving graph representing CPU and memory usage (see Figure 16.4).
Figure 16.4

Figure 16.4 The Graph view of the System Monitor. It shows CPU usage, memory/swap usage, and disk usage. To get this view, select the Resource Monitor tab.


---

### Post by lavinog on 2010-04-14
> **sdowney717 said:**
> [http://www.informit.com/articles/article.aspx?p=770644](http://www.informit.com/articles/article.aspx?p=770644)
according to this, it does show hidden processes.
But when i look for hidden in the menuing all I see is a selection for All processes

Gnome-system-monitor went through some drastic changes since then.  You also shouldn't need to launch it as root.

Show all processes is what you want though.

---

### Post by philinux on 2010-04-14
I had a maxed out cpu the other day and it was a java applet that started it.

---

### Post by french73 on 2010-04-23
Same thing here :
```
ps -eo pcpu,args|sort -rn|head
```
result :
```
86.3 /usr/bin/python /usr/share/checkbox/backend /tmp/checkboxEqxmJh/input /tmp/checkboxEqxmJh/output
44.0 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-7vyoRL/database -nolisten tcp vt7
4.8 gnome-terminal
4.4 bash
%CPU COMMAND
 0.1 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=18
 0.1 metacity
 0.1 gnome-panel
 0.0 [watchdog/1]
 0.0 [watchdog/0]

```
in my mind checkbox = Evolution check process
I'm not use it, then i kill it in start programs and after restart :
```
xxx@xxx:~$ ps -eo pcpu,args|sort -rn|head
 7.2 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-GvUimH/database -nolisten tcp vt7
 5.9 /usr/lib/firefox-3.6.3/firefox-bin
 5.3 bash
 3.2 gnome-terminal
 1.8 nautilus
%CPU COMMAND
 0.3 /usr/bin/pulseaudio --start --log-target=syslog
 0.1 [kswapd0]
 0.1 gnome-panel
 0.0 [watchdog/1]
```
Done :)

Sorry for "my poor english"

---

### Post by lavinog on 2010-04-23
> **french73 said:**
> Same thing here :
```
ps -eo pcpu,args|sort -rn|head
```
result :
```
86.3 /usr/bin/python /usr/share/checkbox/backend /tmp/checkboxEqxmJh/input /tmp/checkboxEqxmJh/output
...

```
in my mind checkbox = Evolution check process
I'm not use it, then i kill it in start programs and after restart :


Here is a bug report for the issue:
[https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636](https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636)

---

