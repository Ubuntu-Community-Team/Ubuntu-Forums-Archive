---
title: "Issue in installing Veeam linux backup agent"
date: 2017-05-18
forum: Installation &amp; Upgrades
---

### Post by lorenzo06 on 2017-05-18
Dear all,
I am a beginner with ubuntu and I am trying to install Veeam backup linux agent on a vmphere virtual server.
My Ubuntu distibution is 16.04. I have been following the guide that Veeam provides ( [https://www.veeam.com/veeam_agent_linux_1_0_user_guide_pg.pdf](https://www.veeam.com/veeam_agent_linux_1_0_user_guide_pg.pdf) ) but I got stuck during the installation process because apitude gives me an error message regarding dependencies.

This is the code I receive when trying to install the software:
```

root@otrs:~# apt-get install -f veeam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 veeam : Depends: veeamsnap (= 1.0.0.944) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
root@otrs:~# apt-get install -f veeamsnap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 veeamsnap : Depends: dkms (>= 2.1.0.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
root@otrs:~# apt-get install -f dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 dkms : Depends: gcc but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---
I tried to look for a solution online but I was not able to find much.
A current solution that is proposed is to run apt-get update, apt-get autoremove, purge or other similar commands. However, none of these worked in my situation.

I hope you will be able to help. Thank you very much in advance for your help!

---

### Post by Xian on 2017-05-18
Post the terminal output from this simplified command:

```
sudo apt-get install -f
```

---

### Post by lorenzo06 on 2017-05-18
Hi Xian,
thank you very much for your reply. I was able to solve the issue by using aptitude instead of apt-get. It seems that aptitute is smarter, it understand the problem and it proposes different solutions. Here is how I solved:
```

root@otrs:/tmp# aptitude install veeam
The following NEW packages will be installed:
  dkms{a} fakeroot{a} gcc{a} gcc-5{ab} libasan2{a} libatomic1{a} libc-dev-bin{a} libc6-dev{ab} libcc1-0{a} libcilkrts5{a} 
  libfakeroot{a} libgcc-5-dev{a} libgomp1{a} libitm1{a} liblsan0{a} libmpx0{a} libquadmath0{a} libtsan0{a} libubsan0{a} 
  linux-libc-dev{a} manpages-dev{a} veeam veeamsnap{a} 
0 packages upgraded, 23 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.8 MB/39.9 MB of archives. After unpacking 115 MB will be used.
The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.23-0ubuntu3) but 2.23-0ubuntu5 is installed.
 gcc-5 : Depends: binutils (>= 2.26.1) but 2.26-8ubuntu2 is installed.
The following actions will resolve these dependencies:


     Keep the following packages at their current version: 
1)     dkms [Not Installed]                                
2)     gcc [Not Installed]                                 
3)     gcc-5 [Not Installed]                               
4)     libc6-dev [Not Installed]                           
5)     veeam [Not Installed]                               
6)     veeamsnap [Not Installed]                           


     Leave the following dependencies unresolved:          
7)     gcc recommends libc6-dev | libc-dev                 
8)     libgcc-5-dev recommends libc6-dev (>= 2.13-0ubuntu6)
9)     gcc-5 recommends libc6-dev (>= 2.13-0ubuntu6)       




Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


     Install the following packages:                                              
1)     gcc-5 [5.3.1-14ubuntu2 (xenial)]                                           
2)     libasan2 [5.3.1-14ubuntu2 (xenial)]                                        
3)     libgcc-5-dev [5.3.1-14ubuntu2 (xenial)]                                    
4)     libmpx0 [5.3.1-14ubuntu2 (xenial)]                                         


     Downgrade the following packages:                                            
5)     cpp-5 [5.4.1-2ubuntu1~16.04 (now, xenial) -> 5.3.1-14ubuntu2 (xenial)]     
6)     gcc-5-base [5.4.1-2ubuntu1~16.04 (now, xenial) -> 5.3.1-14ubuntu2 (xenial)]
7)     libc6 [2.23-0ubuntu5 (now) -> 2.23-0ubuntu3 (xenial)]                      






Accept this solution? [Y/n/q/?] Y
[...]
```

---

