---
title: "How to install Torque on ubuntu 8.04 on a single multicore machine"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by jouke.postma on 2010-01-04
Torque is a batch scheduling system that is often used on clusters. I find it handy to run it on my local machine so I can test run some of my scripts before going on to the cluster. So I started out with an apt-get install torque* and really got into some nasty bugs. Here is a how to for a smoother experience. I mostly used and old post on the subject and the torque installation website:
[http://ubuntuforums.org/showthread.php?t=289767](http://ubuntuforums.org/showthread.php?t=289767)
[http://www.clusterresources.com/torquedocs21/a.ltorquequickstart.shtml](http://www.clusterresources.com/torquedocs21/a.ltorquequickstart.shtml)

1) packages in repositories are broken do not use them, the karmic packages do install, but I did not manage to get them to work.

2) download [http://www.clusterresources.com/downloads/torque/torque-2.4.3.tar.gz](http://www.clusterresources.com/downloads/torque/torque-2.4.3.tar.gz)

3) untar and configure (you probably need the build-essential packages and maybe more for this, my machine had no problems with it). 
```
tar -xzvf torque.tar.gz
cd torque
./configure
```

4) upon success (replace 8 with number of cores in your machine): 
 ```
 make -j 8
  make install
```

5) add /usr/local/lib to ld search path
```
echo /usr/local/lib >> /etc/ld.so.conf
ldconfig
```

6) setup user & cue. Note that although the script will detect your hostname, it does not check if your hostname can be looked up reversely. Use localhost instead if you, like me try this out on a multi core box which is not known bu the dns servers.
Use other admin user than root if so desired. 
```
./torque root localhost
```

6a) check the server name can be looked up reverse: 
```
cat /var/spool/torque/server_name #(should give you the right servername. localhost in my case)
host localhost
```

7) Add localhost to list of nodes (replace 8 with number of cores it has)
```
echo localhost np=8 >> /var/spool/torque/server_priv/nodes
```

8) Tell the node to except the server
```
echo pbs_server = 127.0.0.1 >> /var/spool/torque/mom_priv/config
```

9) add executables to search path. You may also create symbolic links in /usr/bin instead
```
echo PATH=$PATH:/usr/local/bin; export PATH >> /etc/bash.bashrc
```

9) restart the the services
```
pbs_mom
qterm
pbs_server
pbs_sched
```

10) check server and queue named batch
```
ps -aux | grep pbs #check all is running
qstat -q #check the presence of the queue
qmgr -c 'p s' #check server & queue settings
pbsnodes -a  #check if the nodes are listed and up

```
11) set some additional settings for the queu, adjust to your liking
```
qmgr -c "set queue batch resources_default.walltime = 36:00:00"
qmgr -c "set server query_other_jobs = True"
qmgr -c "set queue batch resources_max.ncpus=8"

```
12) Submit job and check if it is running. Don't do this as root, it will not be excepted.
```
echo "sleep 30" | qsub
qstat
```
13) With this setup I got a "no cpus available" messages in the schedulers log file after a single job was submitted. The following queue settings solved my problem. Adjust numbers to your setup.
```
qmgr -c "set queue batch max_running = 8"
qmgr -c "set queue batch resources_max.ncpus = 8"
qmgr -c "set queue batch resources_min.ncpus = 1"
qmgr -c "set queue batch resources_max.nodes = 1"
qmgr -c "set queue batch resources_default.ncpus = 1"
qmgr -c "set queue batch resources_default.neednodes = 1:ppn=1"
qmgr -c "set queue batch resources_default.nodect = 1"
qmgr -c "set queue batch resources_default.nodes = 1"
```

---

### Post by vennyg on 2010-05-18
Thanks for the nicely put together post! it sure did help me install torque successfully on my Ubuntu Hardy

---

