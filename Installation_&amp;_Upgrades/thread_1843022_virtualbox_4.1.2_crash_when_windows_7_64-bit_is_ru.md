---
title: "virtualbox 4.1.2 crash when windows 7 64-bit is running"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by masuch on 2011-09-12
Hi,

I am using virtualbox 4.1.2 to run windows 7 64-bit. 3D support implemented. Sometimes it is going to crash. I cannot figure out where is the problem? Does anybody can help me how to investigate what is wrong ?

thanks

---

### Post by haqking on 2011-09-12
> **masuch said:**
> Hi,

I am using virtualbox 4.1.2 to run windows 7 64-bit. 3D support implemented. Sometimes it is going to crash. I cannot figure out where is the problem? Does anybody can help me how to investigate what is wrong ?

thanks


Check the logs of the VM.

However i hardly ever run x64 VM's in a home environment, in a production environment on a Virtualisation server then yeah.

what memory are you running under the VM ?

remember that hardware is virtualised.

It might be more stable to run a 32 bit version with PAE enabled in the VM if you want to access more memory than the 3.2 lmiit in standard 32 bit

also enable IO APIC and ACPI

---

### Post by masuch on 2011-09-12
[QUOTE=haqking;11244910]

Check the logs of the VM.
 --- This is what I have got but I do not know if that ERROR COM is relevant:

VirtualBox (XP)COM Server 4.1.2 r73507 linux.amd64 (Aug 15 2011 13:17:01) release log
00:00:00.014 main     Log opened 2011-09-12T20:55:36.813765000Z
00:00:00.014 main     OS Product: Linux
00:00:00.014 main     OS Release: 3.0.4-030004-i7
00:00:00.014 main     OS Version: #201108301138 SMP Thu Sep 1 17:01:57 BST 2011
00:00:00.014 main     OS Service Pack: #201108301138 SMP Thu Sep 1 17:01:57 BST 2011
00:00:00.014 main     Executable: /usr/lib/virtualbox/VBoxSVC
00:00:00.014 main     Process ID: 4388
00:00:00.014 main     Package type: LINUX_64BITS_UBUNTU_11_04
00:00:00.123 nspr-2   Loading settings file "/home/u1/.VirtualBox/VirtualBox.xml" with version "1.12-linux"
00:00:00.493 nspr-2   Successfully initialised host USB using sysfs
00:00:00.781 nspr-2   VDInit finished
00:00:00.836 nspr-2   Loading settings file "/home/u1/VirtualBox VMs/windows 7 64bits/windows 7 64bits.vbox" with version "1.12-linux"
00:00:00.867 nspr-2   Loading settings file "/home/u1/VirtualBox VMs/windows 7 32bits/windows 7 32bits.vbox" with version "1.12-linux"
00:00:00.876 nspr-2   Loading settings file "/home/u1/VirtualBox VMs/windows xp 32bits/windows xp 32bits.vbox" with version "1.12-linux"
00:00:00.885 nspr-2   Loading settings file "/home/u1/VirtualBox VMs/windows xp 64bits/windows xp 64bits.vbox" with version "1.12-linux"
00:08:32.148 nspr-4   ERROR [COM]: aRC=VBOX_E_INVALID_VM_STATE (0x80bb0002) aIID={5eaa9319-62fc-4b0a-843c-0cb1940f8a91} aComponent={Machine} aText={Machine is not locked for session (session state: Unlocked)}, preserve=false
00:08:32.350 nspr-2   ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={5eaa9319-62fc-4b0a-843c-0cb1940f8a91} aComponent={SessionMachine} aText={Saved screenshot data is not available (VERR_NOT_SUPPORTED)}, preserve=false



However i hardly ever run x64 VM's in a home environment, in a production environment on a Virtualisation server then yeah.
 --- On my hardware maximus iv extreme R3 i7-2600k overclocked to 5.1 GHz with hd 6990 it is running fine, EXCEPT visualstudio 2010, googleearth and jmonkeyengine - which what is mostly interesting me :-(( - So, no way for development - but this is probably problem because of virtualbox openGL 3D which does not work properly according to my experience :-(

what memory are you running under the VM ?
 --- for this instance I allowed 4GB (from 16GB), (4 processors)

remember that hardware is virtualised.
 --- BIOS is setup for virtualization - there is only one option , so I do not know if I need to switch on something else ?

It might be more stable to run a 32 bit version with PAE enabled in the VM if you want to access more memory than the 3.2 limit in standard 32 bit
 --- at this moment my 32 bit version with PAE is damaged - I do not see login dialog - so I have to take it from backup. But it rarely crashed as well. 

also enable IO APIC and ACPI
 --- in virtualbox IO APIC enabled
 --- in BIOS ACPI enabled


please let me know what else should I checked or changed or does exist some switch on more verbose log tracing of virtualbox or something else ?

thanks for any advice

---

### Post by haqking on 2011-09-12
> **masuch said:**
> [QUOTE=haqking;11244910]

Check the logs of the VM.
 --- This is what I have got but I do not know if that ERROR COM is relevant:

VirtualBox (XP)COM Server 4.1.2 r73507 linux.amd64 (Aug 15 2011 13:17:01) release log
00:00:00.014 main     Log opened 2011-09-12T20:55:36.813765000Z
00:00:00.014 main     OS Product: Linux
00:00:00.014 main     OS Release: 3.0.4-030004-i7
00:00:00.014 main     OS Version: #201108301138 SMP Thu Sep 1 17:01:57 BST 2011
00:00:00.014 main     OS Service Pack: #201108301138 SMP Thu Sep 1 17:01:57 BST 2011
00:00:00.014 main     Executable: /usr/lib/virtualbox/VBoxSVC
00:00:00.014 main     Process ID: 4388
00:00:00.014 main     Package type: LINUX_64BITS_UBUNTU_11_04
00:00:00.123 nspr-2   Loading settings file "/home/u1/.VirtualBox/VirtualBox.xml" with version "1.12-linux"
00:00:00.493 nspr-2   Successfully initialised host USB using sysfs
00:00:00.781 nspr-2   VDInit finished
00:00:00.836 nspr-2   Loading settings file "/home/u1/VirtualBox VMs/windows 7 64bits/windows 7 64bits.vbox" with version "1.12-linux"
00:00:00.867 nspr-2   Loading settings file "/home/u1/VirtualBox VMs/windows 7 32bits/windows 7 32bits.vbox" with version "1.12-linux"
00:00:00.876 nspr-2   Loading settings file "/home/u1/VirtualBox VMs/windows xp 32bits/windows xp 32bits.vbox" with version "1.12-linux"
00:00:00.885 nspr-2   Loading settings file "/home/u1/VirtualBox VMs/windows xp 64bits/windows xp 64bits.vbox" with version "1.12-linux"
00:08:32.148 nspr-4   ERROR [COM]: aRC=VBOX_E_INVALID_VM_STATE (0x80bb0002) aIID={5eaa9319-62fc-4b0a-843c-0cb1940f8a91} aComponent={Machine} aText={Machine is not locked for session (session state: Unlocked)}, preserve=false
00:08:32.350 nspr-2   ERROR [COM]: aRC=VBOX_E_IPRT_ERROR (0x80bb0005) aIID={5eaa9319-62fc-4b0a-843c-0cb1940f8a91} aComponent={SessionMachine} aText={Saved screenshot data is not available (VERR_NOT_SUPPORTED)}, preserve=false



However i hardly ever run x64 VM's in a home environment, in a production environment on a Virtualisation server then yeah.
 --- On my hardware maximus iv extreme R3 i7-2600k overclocked to 5.1 GHz with hd 6990 it is running fine, EXCEPT visualstudio 2010, googleearth and jmonkeyengine - which what is mostly interesting me :-(( - So, no way for development - but this is probably problem because of virtualbox openGL 3D which does not work properly according to my experience :-(

what memory are you running under the VM ?
 --- for this instance I allowed 4GB (from 16GB), (4 processors)

remember that hardware is virtualised.
 --- BIOS is setup for virtualization - there is only one option , so I do not know if I need to switch on something else ?

It might be more stable to run a 32 bit version with PAE enabled in the VM if you want to access more memory than the 3.2 limit in standard 32 bit
 --- at this moment my 32 bit version with PAE is damaged - I do not see login dialog - so I have to take it from backup. But it rarely crashed as well. 

also enable IO APIC and ACPI
 --- in virtualbox IO APIC enabled
 --- in BIOS ACPI enabled


please let me know what else should I checked or changed or does exist some switch on more verbose log tracing of virtualbox or something else ?

thanks for any advice

that is the virtualbox logs, i meant the logs in the OS as it might be the VM OS which is crashing and not virtual box itself.

---

### Post by masuch on 2011-09-12
This is part of :
C:\Users\u2\AppData\Local\Temp\WERD8C9.tmp.WERInternalMetadata.xml

-<ParentProcessInformation> <ParentProcessId>3860</ParentProcessId> <ParentProcessPath>C:\Windows\explorer.exe</ParentProcessPath> <ParentProcessCmdLine>C:\Windows\Explorer.EXE</ParentProcessCmdLine> </ParentProcessInformation> -<ProblemSignatures> <EventType>APPCRASH</EventType> <Parameter0>msinfo32.exe</Parameter0> <Parameter1>6.1.7601.17514</Parameter1> <Parameter2>4ce79731</Parameter2> <Parameter3>MFC42u.dll</Parameter3> <Parameter4>6.6.8064.0</Parameter4> <Parameter5>4d79bfc6</Parameter5> <Parameter6>c0000005</Parameter6> <Parameter7>00000000000040ce</Parameter7> </ProblemSignatures> -<DynamicSignatures> <Parameter1>6.1.7601.2.1.0.256.1</Parameter1> <Parameter2>2057</Parameter2> <Parameter22>614a</Parameter22> <Parameter23>614a7015bc6057adb874c5b22b5ba171</Parameter23> <Parameter24>0bfb</Parameter24> <Parameter25>0bfba164e6790c48047f5e5bb77ad231</Parameter25> </DynamicSignatures> -<SystemInformation> <MID>82EDA1BA-6B56-4D17-A8D6-B8E9FBB393FA</MID> <SystemManufacturer>innotek GmbH</SystemManufacturer> <SystemProductName>VirtualBox</SystemProductName> <BIOSVersion>VirtualBox</BIOSVersion> </SystemInformation> </WERReportMetadata>


c:\Windows\Logs\CBS\CBS.log does not contain any virtualbox or vbox word.

Let me know what specific log/s files should I find or key works to look for ?

One thing is strange - I cannot start any admin software ... to look into system logs , application logs - is there any way how to manually look into it ?

---

### Post by haqking on 2011-09-12
> **masuch said:**
> This is part of :
C:\Users\u2\AppData\Local\Temp\WERD8C9.tmp.WERInternalMetadata.xml

-<ParentProcessInformation> <ParentProcessId>3860</ParentProcessId> <ParentProcessPath>C:\Windows\explorer.exe</ParentProcessPath> <ParentProcessCmdLine>C:\Windows\Explorer.EXE</ParentProcessCmdLine> </ParentProcessInformation> -<ProblemSignatures> <EventType>APPCRASH</EventType> <Parameter0>msinfo32.exe</Parameter0> <Parameter1>6.1.7601.17514</Parameter1> <Parameter2>4ce79731</Parameter2> <Parameter3>MFC42u.dll</Parameter3> <Parameter4>6.6.8064.0</Parameter4> <Parameter5>4d79bfc6</Parameter5> <Parameter6>c0000005</Parameter6> <Parameter7>00000000000040ce</Parameter7> </ProblemSignatures> -<DynamicSignatures> <Parameter1>6.1.7601.2.1.0.256.1</Parameter1> <Parameter2>2057</Parameter2> <Parameter22>614a</Parameter22> <Parameter23>614a7015bc6057adb874c5b22b5ba171</Parameter23> <Parameter24>0bfb</Parameter24> <Parameter25>0bfba164e6790c48047f5e5bb77ad231</Parameter25> </DynamicSignatures> -<SystemInformation> <MID>82EDA1BA-6B56-4D17-A8D6-B8E9FBB393FA</MID> <SystemManufacturer>innotek GmbH</SystemManufacturer> <SystemProductName>VirtualBox</SystemProductName> <BIOSVersion>VirtualBox</BIOSVersion> </SystemInformation> </WERReportMetadata>


c:\Windows\Logs\CBS\CBS.log does not contain any virtualbox or vbox word.

Let me know what specific log/s files should I find or key works to look for ?

One thing is strange - I cannot start any admin software ... to look into system logs , application logs - is there any way how to manually look into it ?


yeah i meant the logs in event viewer, system, application etc for signs of why it crashed.

what do you mean you cant ? you click and they wont run ? and error message ?

have you tried launching it manually from run command ?

i think it is **eventvwr** ifi remember correctly, from command prompt or run command.

you coudl also start up a new mmc and add the snapins if your shortcuts have issues ?

Thing is , is this a Windows VM issue or Virtual box in Ubuntu issue ?

if it is a windows in a VM issue you might want to check out a windows dedicated forum

---

### Post by westie457 on 2011-09-12
@masuch> One thing is strange - I cannot start any admin software ... to look into system logs , application logs - is there any way how to manually look into it ?

Not knowing as much about virtualisation as those already helping you and I could be wrong as well. The quote above suggests to me that your Virtual Windows has some malware in it. Are you able to boot the Windows into safe mode to check the logs and use admin tools?

---

### Post by masuch on 2011-09-12
OK, I understand your point. But it is really not going to start at all - no message/s - nothing - just blinking hard disk but nothing start - I have never seen this before in windows 7 - it is not even in task manager (no eventvwr , no mmc) - just appears in taskman for 2 seconds and disappear - but it is first thing what I have got to work.

---

### Post by haqking on 2011-09-12
> **masuch said:**
> OK, I understand your point. But it is really not going to start at all - no message/s - nothing - just blinking hard disk but nothing start - I have never seen this before in windows 7 - it is not even in task manager (no eventvwr , no mmc) - just appears in taskman for 2 seconds and disappear - but it is first thing what I have got to work.


Well if iwas in your postion.  I would switch to my clone or snapshot of the V<.

If you havent got one, then there lies in a lesson...LOL ;-)

Or restore from backup of your VM's ?

if none of this is possible, i would be inclined to do a reinstall.  once installed taking a snapshot then adding one thing and trying it etc.

also i see earlier you are assigning 4 processors to the VM ?

calm things down a little on the VM specs and slowly add one by one a setting or increase and software etc.

and i take it that VT-x is enabled under acceleration tab of the VM, and if so then possibly remove it as well as the APCI and IO APIC etc

---

### Post by masuch on 2011-09-12
> **westie457 said:**
> @masuch

Not knowing as much about virtualisation as those already helping you and I could be wrong as well. The quote above suggests to me that your Virtual Windows has some malware in it. Are you able to boot the Windows into safe mode to check the logs and use admin tools?

nope. Any admin tools is not possible to start (even from admin cmd.exe (that is actually only one admin application which is possible to start)) - it looks like always something is gone kill any admin application.

---

### Post by haqking on 2011-09-12
> **masuch said:**
> nope. Any admin tools is not possible to start (even from admin cmd.exe (that is actually only one admin application which is possible to start)) - it looks like always something is gone kill any admin application.


Safe mode  ?

system restore ?

snapshot ?

clone ?

backups ?

---

### Post by masuch on 2011-09-12
> **haqking said:**
> Well if iwas in your postion.  I would switch to my clone or snapshot of the V<.

If you havent got one, then there lies in a lesson...LOL ;-)

Or restore from backup of your VM's ?

if none of this is possible, i would be inclined to do a reinstall.  once installed taking a snapshot then adding one thing and trying it etc.

also i see earlier you are assigning 4 processors to the VM ?

calm things down a little on the VM specs and slowly add one by one a setting or increase and software etc.

and i take it that VT-x is enabled under acceleration tab of the VM, and if so then possibly remove it as well as the APCI and IO APIC etc


I have some backup/s so I am gone solve it by my older backup firstly - after that I am gonna continue with log/s investigation - sorry about this unexpected behavior. I did not have so much fun in virtualbox before :-) I have been too focus on jmonkeyengine and I did not noticed that admin appls do not work :-)

---

### Post by haqking on 2011-09-12
> **masuch said:**
> I have some backup/s so I am gone solve it by my older backup firstly - after that I am gonna continue with log/s investigation - sorry about this unexpected behavior. I did not have so much fun in virtualbox before :-) I have been too focus on jmonkeyengine and I did not noticed that admin appls do not work :-)


No worries, hope you get it resolved.

Backups are key...ALWAYS ;-)

good luck

peace

---

### Post by masuch on 2011-09-12
> **westie457 said:**
> @masuch

Not knowing as much about virtualisation as those already helping you and I could be wrong as well. The quote above suggests to me that your Virtual Windows has some malware in it. Are you able to boot the Windows into safe mode to check the logs and use admin tools?

I am curious, according to what I are you suggesting that I have malware? Could you post more information about it ? 
thanks for any clue.

---

### Post by haqking on 2011-09-12
> **masuch said:**
> I am curious, according to what I are you suggesting that I have malware? Could you post more information about it ? 
thanks for any clue.


yeah i mean its possible.

Loss of Admin tools access not necesarily symptomatic of malware though but it could be.

Does the VM have external access to internet ? RDP or VNC enabled ?i mean if its on a LAn machine and doesnt have any remote services enabled then its unikely unless you installed infected software etc.

Do you have AV on it ?

again it comes back to your backups ;-)

---

### Post by masuch on 2011-09-12
> **haqking said:**
> yeah i mean its possible.

Loss of Admin tools access not necesarily symptomatic of malware though but it could be.

Does the VM have external access to internet ? RDP or VNC enabled ?i mean if its on a LAn machine and doesnt have any remote services enabled then its unikely unless you installed infected software etc.
 --- yes it is connecting to internet , no vnc no rdp. I will take a look deeply if some remote service/s are running.

Do you have AV on it ?
 --- i have avg latest updates.

again it comes back to your backups ;-)
 --- first backup disappointed me - same behavior :-)

---

### Post by haqking on 2011-09-12
> **masuch said:**
> --- first backup disappointed me - same behavior :-)


ok you havent come back with answer to anything else mentioned.

such as vt-x etc

see post #9 and post #11

---

### Post by masuch on 2011-09-13
> **haqking said:**
> ok you havent come back with answer to anything else mentioned.

such as vt-x etc

see post #9 and post #11

3 of 64 bits backups does not work - same behavior, 3 of 32 bits backups are damaged or does not work because of different reason. I am still working on 32 and 64 bit versions. I will be back when I have got some discuss able results :-)

---

### Post by masuch on 2011-09-13
> **masuch said:**
> 3 of 64 bits backups does not work - same behavior, 3 of 32 bits backups are damaged or does not work because of different reason. I am still working on 32 and 64 bit versions. I will be back when I have got some discuss able results :-)

I have read a lot of windows forums about those problems - it looks that a lot of users had/have it from version of windows xp - even if not in virtual mode. It seems that it is some bigger issue/s more deeply rooted in windows OSes :-)
Unfortunately most of us who have these problems did not find solution - I gave a try to solve it by many ways but none of them work :confused:

---

### Post by masuch on 2011-10-01
Hi,

Thank you all who tried to help me !!!

One out of four memory modules has failed.

At this time I have to start from the beginning because probably all of my .vdi files are now damaged because have been backup within invalid memory module.
I am gonging to let this thread open until I have finished the installation from the scratch and testing of running w764bit without problems.

cheers,
M.

---

### Post by haqking on 2011-10-01
> **masuch said:**
> Hi,

Thank you all who tried to help me !!!

One out of four memory modules has failed.

At this time I have to start from the beginning because probably all of my .vdi files are now damaged because have been backup within invalid memory module.
I am gonging to let this thread open until I have finished the installation from the scratch and testing of running w764bit without problems.

cheers,
M.

A corrupt memory module wont effect a .vdi in terms of a backup,  Just stick in a new module and away you go.  When you back something up you do it incase of hardware failure, you dont backup the hardware issues with the backup when you do it.

---

### Post by masuch on 2011-10-01
> **haqking said:**
> A corrupt memory module wont effect a .vdi in terms of a backup,  Just stick in a new module and away you go.  When you back something up you do it incase of hardware failure, you dont backup the hardware issues with the backup when you do it.

That's sound nice but everytime when I made a copy of .vdi files , the sha1sum had different number/s - because of failed memory module. 

I have been trying to solve it on :
[http://www.linuxquestions.org/questions/linux-newbie-8/md5sum-sha1sum-are-different-after-copy-file-s-by-cp-command-krusader-or-nautilus-904889/](http://www.linuxquestions.org/questions/linux-newbie-8/md5sum-sha1sum-are-different-after-copy-file-s-by-cp-command-krusader-or-nautilus-904889/)

I understand that I cannot backup hardware issue but How I can be sure that copied files were not damaged within the copy process (I have been always using only cp command to backup .vdi files) .
  Whole copy process is always going through the memory and if memory has error ? I know there is a parity check control on hardware level but only for one bit (And there is possibility that memory could have error but parity control does not have to discover it - according to information 20 years old when I have been programming in assembler :-) ,maybe now it is more sophisticated). And checking on software level I do not know how is it in linux (windows has switch (verify on) to check files "integrity" within copy operation) ?

Could you please explain in more details how I can be sure that .vdi files are ok ?

Sorry for asking , but I have more that 60 .vdi files of different linux distributions (just trying how does it work and "looks and feel") and more than 20 .vdi windows files, and Solaris UNIX and BSD .vdi files - So , I hope you understand my concern.

thanks a lot

---

### Post by masuch on 2011-10-04
Hi,

Thanks to all who participate to solve this problem.
After I removed defective memory module I did not get into any crash problem.
(Unfortunately almost all of current and backup .vdi files have been corrupted.)

Thanks again.
Cheers,

---

