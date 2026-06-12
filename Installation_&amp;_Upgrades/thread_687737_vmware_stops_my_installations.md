---
title: "vmware stops my installations"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Seikmann on 2008-02-04
So, I have tried to install VMware. it wanted a serial, so I just quitted the whole sheebang. 
When I now tries to install anything else, I get this errormessage:
```
1	seik@eientei:~$ sudo aptitude install ssh  
2	[sudo] password for seik:  
3	E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  
4	Reading package lists... Done  
5	Building dependency tree  
6	Reading state information... Done  
7	Reading extended state information  
8	Initializing package states... Done  
9	Building tag database... Done  
10	E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  
11	seik@eientei:~$ dpkg --configure -a  
12	dpkg: requested operation requires superuser privilege  
13	seik@eientei:~$ sudo -s -H  
14	root@eientei:/home/seik# dpkg --configure -a  
15	Setting up vmware-server (1.0.4-1gutsy2) ...  
16	Making sure services for VMware Server are stopped.  
17	  
18	Stopping VMware services:  
19	   Virtual machine monitor                                             done  
20	  
21	Do you want networking for your virtual machines? (yes/no/help) [yes]  
22	  
23	Configuring a bridged network for vmnet0.  
24	  
25	Your computer has multiple ethernet network interfaces available: eth0, wlan0.  
26	Which one do you want to bridge to vmnet0? [eth0]  
27	  
28	The following bridged networks have been defined:  
29	  
30	. vmnet0 is bridged to eth0  
31	  
32	Do you wish to configure another bridged network? (yes/no) [no]  
33	  
34	Do you want to be able to use NAT networking in your virtual machines? (yes/no)  
35	[yes]  
36	  
37	Configuring a NAT network for vmnet8.  
38	  
39	Do you want this program to probe for an unused private subnet? (yes/no/help)  
40	[yes]  
41	  
42	Probing for an unused private subnet (this can take some time)...  
43	  
44	The subnet 192.168.128.0/255.255.255.0 appears to be unused.  
45	  
46	The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to  
47	install already exists.  Overwrite? [yes]  
48	  
49	The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to  
50	install already exists.  Overwrite? [yes]  
51	  
52	The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to  
53	install already exists.  Overwrite? [yes]  
54	  
55	The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install  
56	already exists.  Overwrite? [yes]  
57	  
58	The following NAT networks have been defined:  
59	  
60	. vmnet8 is a NAT network on private subnet 192.168.128.0.  
61	  
62	Do you wish to configure another NAT network? (yes/no) [no]  
63	  
64	Do you want to be able to use host-only networking in your virtual machines?  
65	[yes]  
66	  
67	Configuring a host-only network for vmnet1.  
68	  
69	Do you want this program to probe for an unused private subnet? (yes/no/help)  
70	[yes]  
71	  
72	Probing for an unused private subnet (this can take some time)...  
73	  
74	The subnet 172.16.53.0/255.255.255.0 appears to be unused.  
75	  
76	The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to  
77	install already exists.  Overwrite? [yes]  
78	  
79	The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to  
80	install already exists.  Overwrite? [yes]  
81	  
82	The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to  
83	install already exists.  Overwrite? [yes]  
84	  
85	The following host-only networks have been defined:  
86	  
87	. vmnet1 is a host-only network on private subnet 172.16.53.0.  
88	  
89	Do you wish to configure another host-only network? (yes/no) [no]  
90	  
91	Generating SSL Server Certificate  
92	  
93	Starting VMware services:  
94	   Virtual machine monitor                                             done  
95	   Virtual ethernet                                                    done  
96	   Bridged networking on /dev/vmnet0                                   done  
97	   Host-only networking on /dev/vmnet1 (background)                    done  
98	   Host-only networking on /dev/vmnet8 (background)                    done  
99	   NAT service on /dev/vmnet8                                          done  
100	  
101	dpkg: error processing vmware-server (--configure):  
102	 subprocess post-installation script returned error exit status 10  
103	Errors were encountered while processing:  
104	 vmware-server  
105	root@eientei:/home/seik#  
106	 

```

---

### Post by zvacet on 2008-02-04
```
sudo apt-get -f install
```

If that doesn´t help remove vmware-server from synaptic and install it  again.If you can not remove it with synaptic run 

```
sudo apt-get --purge remove vmware-server
```

or 

```
sudo dpkg --remove --force-remove-reinstreq vmware-server
```

When you reinstall it type this serial 98EDN-YPG66-2C624-42HA9

---

