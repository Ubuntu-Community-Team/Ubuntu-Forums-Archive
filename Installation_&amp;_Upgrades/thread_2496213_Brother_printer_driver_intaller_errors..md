---
title: "Brother printer driver intaller errors."
date: 2024-03-18
forum: Installation &amp; Upgrades
---

### Post by knight69 on 2024-03-18
Running Ubuntu 20.04 on a desktop computer, I am attempting to reinstall the printer drivers for a Brother HL-3170CDW printer. This printer was previously installed and working perfectly unlit the latest Ubuntu update.When reinstalling using the Brother supplied driver installer, I get several error messages during the installation, most claiming the software couldn't find the deb packages it needed for installation in spite of them being in the same directory with the installer. Toward the end, it requests an IP address for my network printer bu after entering the correct IP address and printing a test file, the printer fails to respond. [IMG]https://ubuntuforums.org/;base64,d2F5bmVAZ3Vlc3Q6fi9VdGlsaXRpZXMvQnJvdGhlciBQcmludGVyJCBzdWRvIGJhc2ggbGludXgtYnJwcmludGVyLWluc3RhbGxlci0yLjIuMy0xCklucHV0IG1vZGVsIG5hbWUgLT5ITC0zMTcwQ0RXCgpZb3UgYXJlIGdvaW5nIHRvIGluc3RhbGwgZm9sbG93aW5nIHBhY2thZ2VzLgogICBobDMxNzBjZHdscHItMS4xLjItMS5pMzg2LmRlYgogICBobDMxNzBjZHdjdXBzd3JhcHBlci0xLjEuNC0wLmkzODYuZGViCk9LPyBbeS9OXSAtPnkKCkhpdDoxIGh0dHA6Ly91cy5hcmNoaXZlLnVidW50dS5jb20vdWJ1bnR1IGZvY2FsIEluUmVsZWFzZQpIaXQ6MiBodHRwOi8vdXMuYXJjaGl2ZS51YnVudHUuY29tL3VidW50dSBmb2NhbC11cGRhdGVzIEluUmVsZWFzZQpIaXQ6MyBodHRwOi8vdXMuYXJjaGl2ZS51YnVudHUuY29tL3VidW50dSBmb2NhbC1iYWNrcG9ydHMgSW5SZWxlYXNlCkhpdDo0IGh0dHA6Ly9zZWN1cml0eS51YnVudHUuY29tL3VidW50dSBmb2NhbC1zZWN1cml0eSBJblJlbGVhc2UKUmVhZGluZyBwYWNrYWdlIGxpc3RzLi4uIERvbmUKUmVhZGluZyBwYWNrYWdlIGxpc3RzLi4uIERvbmUKQnVpbGRpbmcgZGVwZW5kZW5jeSB0cmVlICAgICAgIApSZWFkaW5nIHN0YXRlIGluZm9ybWF0aW9uLi4uIERvbmUKUGFja2FnZSBpYTMyLWxpYnMgaXMgbm90IGF2YWlsYWJsZSwgYnV0IGlzIHJlZmVycmVkIHRvIGJ5IGFub3RoZXIgcGFja2FnZS4KVGhpcyBtYXkgbWVhbiB0aGF0IHRoZSBwYWNrYWdlIGlzIG1pc3NpbmcsIGhhcyBiZWVuIG9ic29sZXRlZCwgb3IKaXMgb25seSBhdmFpbGFibGUgZnJvbSBhbm90aGVyIHNvdXJjZQpIb3dldmVyIHRoZSBmb2xsb3dpbmcgcGFja2FnZXMgcmVwbGFjZSBpdDoKICBsaWIzMnoxCgpFOiBQYWNrYWdlICdpYTMyLWxpYnMnIGhhcyBubyBpbnN0YWxsYXRpb24gY2FuZGlkYXRlCmRwa2cgLXggaGwzMTcwY2R3bHByLTEuMS4yLTEuaTM4Ni5kZWIgLwpkcGtnIC14IGhsMzE3MGNkd2N1cHN3cmFwcGVyLTEuMS40LTAuaTM4Ni5kZWIgLwpjcDogY2Fubm90IHN0YXQgJy9ob21lL3dheW5lL1V0aWxpdGllcy9Ccm90aGVyJzogTm8gc3VjaCBmaWxlIG9yIGRpcmVjdG9yeQpjcDogY2Fubm90IHN0YXQgJ1ByaW50ZXIvaGwzMTcwY2R3bHByLTEuMS4yLTEuaTM4Ni5kZWInOiBObyBzdWNoIGZpbGUgb3IgZGlyZWN0b3J5CmRwa2ctZGViOiBlcnJvcjogZmFpbGVkIHRvIHJlYWQgYXJjaGl2ZSAnaGwzMTcwY2R3bHByLTEuMS4yLTEuaTM4Ni5kZWInOiBObyBzdWNoIGZpbGUgb3IgZGlyZWN0b3J5CmRwa2ctZGViOiBlcnJvcjogZmFpbGVkIHRvIHJlYWQgYXJjaGl2ZSAnaGwzMTcwY2R3bHByLTEuMS4yLTEuaTM4Ni5kZWInOiBObyBzdWNoIGZpbGUgb3IgZGlyZWN0b3J5CmxpbnV4LWJycHJpbnRlci1pbnN0YWxsZXItMi4yLjMtMTogbGluZSAyMzE4OiBERUJJQU4vY29udHJvbC50bXA6IE5vIHN1Y2ggZmlsZSBvciBkaXJlY3RvcnkKY2F0OiBERUJJQU4vY29udHJvbDogTm8gc3VjaCBmaWxlIG9yIGRpcmVjdG9yeQptdjogY2Fubm90IHN0YXQgJ0RFQklBTi9jb250cm9sLnRtcCc6IE5vIHN1Y2ggZmlsZSBvciBkaXJlY3RvcnkKZHBrZy1kZWI6IGVycm9yOiBmYWlsZWQgdG8gb3BlbiBwYWNrYWdlIGluZm8gZmlsZSAnLi9icm90aGVyX2RyaXZlcl9wYWNrZGlyL0RFQklBTi9jb250cm9sJyBmb3IgcmVhZGluZzogTm8gc3VjaCBmaWxlIG9yIGRpcmVjdG9yeQpkcGtnIC1iIC4vYnJvdGhlcl9kcml2ZXJfcGFja2RpciBobDMxNzBjZHdscHItMS4xLjItMWEuaTM4Ni5kZWIKY3A6IGNhbm5vdCBzdGF0ICcvaG9tZS93YXluZS9VdGlsaXRpZXMvQnJvdGhlcic6IE5vIHN1Y2ggZmlsZSBvciBkaXJlY3RvcnkKY3A6IGNhbm5vdCBzdGF0ICdQcmludGVyL2hsMzE3MGNkd2N1cHN3cmFwcGVyLTEuMS40LTAuaTM4Ni5kZWInOiBObyBzdWNoIGZpbGUgb3IgZGlyZWN0b3J5CmRwa2ctZGViOiBlcnJvcjogZmFpbGVkIHRvIHJlYWQgYXJjaGl2ZSAnaGwzMTcwY2R3Y3Vwc3dyYXBwZXItMS4xLjQtMC5pMzg2LmRlYic6IE5vIHN1Y2ggZmlsZSBvciBkaXJlY3RvcnkKZHBrZy1kZWI6IGVycm9yOiBmYWlsZWQgdG8gcmVhZCBhcmNoaXZlICdobDMxNzBjZHdjdXBzd3JhcHBlci0xLjEuNC0wLmkzODYuZGViJzogTm8gc3VjaCBmaWxlIG9yIGRpcmVjdG9yeQpsaW51eC1icnByaW50ZXItaW5zdGFsbGVyLTIuMi4zLTE6IGxpbmUgMjM0NTogREVCSUFOL2NvbnRyb2wudG1wOiBObyBzdWNoIGZpbGUgb3IgZGlyZWN0b3J5CmNhdDogREVCSUFOL2NvbnRyb2w6IE5vIHN1Y2ggZmlsZSBvciBkaXJlY3RvcnkKbXY6IGNhbm5vdCBzdGF0ICdERUJJQU4vY29udHJvbC50bXAnOiBObyBzdWNoIGZpbGUgb3IgZGlyZWN0b3J5CmRwa2ctZGViOiBlcnJvcjogZmFpbGVkIHRvIG9wZW4gcGFja2FnZSBpbmZvIGZpbGUgJy4vYnJvdGhlcl9kcml2ZXJfcGFja2Rpci9ERUJJQU4vY29udHJvbCcgZm9yIHJlYWRpbmc6IE5vIHN1Y2ggZmlsZSBvciBkaXJlY3RvcnkKZHBrZyAtYiAuL2Jyb3RoZXJfZHJpdmVyX3BhY2tkaXIgaGwzMTcwY2R3Y3Vwc3dyYXBwZXItMS4xLjQtMGEuaTM4Ni5kZWIKbXY6IHRhcmdldCAnUHJpbnRlcicgaXMgbm90IGEgZGlyZWN0b3J5Cm12OiB0YXJnZXQgJ1ByaW50ZXInIGlzIG5vdCBhIGRpcmVjdG9yeQpsaW51eC1icnByaW50ZXItaW5zdGFsbGVyLTIuMi4zLTE6IGxpbmUgMjM5ODogY2Q6IHRvbyBtYW55IGFyZ3VtZW50cwpkcGtnIC1pIC0tZm9yY2UtYWxsIGhsMzE3MGNkd2xwci0xLjEuMi0xYS5pMzg2LmRlYgpkcGtnOiBlcnJvcjogY2Fubm90IGFjY2VzcyBhcmNoaXZlICdobDMxNzBjZHdscHItMS4xLjItMWEuaTM4Ni5kZWInOiBObyBzdWNoIGZpbGUgb3IgZGlyZWN0b3J5CmRwa2cgLWkgLS1mb3JjZS1hbGwgaGwzMTcwY2R3Y3Vwc3dyYXBwZXItMS4xLjQtMGEuaTM4Ni5kZWIKZHBrZzogZXJyb3I6IGNhbm5vdCBhY2Nlc3MgYXJjaGl2ZSAnaGwzMTcwY2R3Y3Vwc3dyYXBwZXItMS4xLjQtMGEuaTM4Ni5kZWInOiBObyBzdWNoIGZpbGUgb3IgZGlyZWN0b3J5CiMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyNsczogY2Fubm90IGFjY2VzcyAnL3Vzci9zaGFyZS9wcGQvKi5wcGQnOiBObyBzdWNoIGZpbGUgb3IgZGlyZWN0b3J5CmxzOiBjYW5ub3QgYWNjZXNzICcvdXNyL3NoYXJlL2N1cHMvbW9kZWwvKi5wcGQnOiBObyBzdWNoIGZpbGUgb3IgZGlyZWN0b3J5CiMKCjA6IGJlaAoxOiBodHRwcwoyOiBjdXBzLWJyZjovCjM6IGhwCjQ6IGh0dHAKNTogbHBkCjY6IHNlcmlhbDovZGV2L3R0eVMwP2JhdWQ9MTE1MjAwCjc6IHNvY2tldAo4OiBpcHAKOTogaXBwcwoxMDogcGFyYWxsZWw6L2Rldi9scDAKMTE6IGhwZmF4CjEyIChJKTogU3BlY2lmeSBJUCBhZGRyZXNzLgoxMyAoQSk6IEF1dG8uICh1c2I6Ly9kZXYvdXNibHAwKQoKc2VsZWN0IHRoZSBudW1iZXIgb2YgZGVzdGluYXRpb24gRGV2aWNlIFVSSS4gLT4xMgoKIGVudGVyIElQIGFkZHJlc3MgLT4xOTIuMTY4LjEuMjAwCmxwYWRtaW4gLXAgSEwzMTcwQ0RXIC12IHNvY2tldDovLzE5Mi4xNjguMS4yMDAgLUUKVGVzdCBQcmludD8gW3kvTl0gLT55Cgp3YWl0IDVzLgpscHIgLVAgSEwzMTcwQ0RXIC91c3Ivc2hhcmUvY3Vwcy9kYXRhL3Rlc3RwcmludApIaXQgRW50ZXIvUmV0dXJuIGtleS4Kcm1kaXI6IGZhaWxlZCB0byByZW1vdmUgJy90bXAvYnJwcmludGVyLWluc3RhbGxlcl9PcGRPeFQnOiBEaXJlY3Rvcnkgbm90IGVtcHR5CndheW5lQGd1ZXN0On4vVXRpbGl0aWVzL0Jyb3RoZXIgUHJpbnRlciQgCgoK[/IMG]

Installation messages are as follows:[INDENT]wayne@guest:~/Utilities/Brother Printer$ sudo bash linux-brprinter-installer-2.2.3-1
Input model name ->HL-3170CDW

You are going to install following packages.
   hl3170cdwlpr-1.1.2-1.i386.deb
   hl3170cdwcupswrapper-1.1.4-0.i386.deb
OK? [y/N] ->y

Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1

E: Package 'ia32-libs' has no installation candidate
dpkg -x hl3170cdwlpr-1.1.2-1.i386.deb /
dpkg -x hl3170cdwcupswrapper-1.1.4-0.i386.deb /
cp: cannot stat '/home/wayne/Utilities/Brother': No such file or directory
cp: cannot stat 'Printer/hl3170cdwlpr-1.1.2-1.i386.deb': No such file or directory
dpkg-deb: error: failed to read archive 'hl3170cdwlpr-1.1.2-1.i386.deb': No such file or directory
dpkg-deb: error: failed to read archive 'hl3170cdwlpr-1.1.2-1.i386.deb': No such file or directory
linux-brprinter-installer-2.2.3-1: line 2318: DEBIAN/control.tmp: No such file or directory
cat: DEBIAN/control: No such file or directory
mv: cannot stat 'DEBIAN/control.tmp': No such file or directory
dpkg-deb: error: failed to open package info file './brother_driver_packdir/DEBIAN/control' for reading: No such file or directory
dpkg -b ./brother_driver_packdir hl3170cdwlpr-1.1.2-1a.i386.deb
cp: cannot stat '/home/wayne/Utilities/Brother': No such file or directory
cp: cannot stat 'Printer/hl3170cdwcupswrapper-1.1.4-0.i386.deb': No such file or directory
dpkg-deb: error: failed to read archive 'hl3170cdwcupswrapper-1.1.4-0.i386.deb': No such file or directory
dpkg-deb: error: failed to read archive 'hl3170cdwcupswrapper-1.1.4-0.i386.deb': No such file or directory
linux-brprinter-installer-2.2.3-1: line 2345: DEBIAN/control.tmp: No such file or directory
cat: DEBIAN/control: No such file or directory
mv: cannot stat 'DEBIAN/control.tmp': No such file or directory
dpkg-deb: error: failed to open package info file './brother_driver_packdir/DEBIAN/control' for reading: No such file or directory
dpkg -b ./brother_driver_packdir hl3170cdwcupswrapper-1.1.4-0a.i386.deb
mv: target 'Printer' is not a directory
mv: target 'Printer' is not a directory
linux-brprinter-installer-2.2.3-1: line 2398: cd: too many arguments
dpkg -i --force-all hl3170cdwlpr-1.1.2-1a.i386.deb
dpkg: error: cannot access archive 'hl3170cdwlpr-1.1.2-1a.i386.deb': No such file or directory
dpkg -i --force-all hl3170cdwcupswrapper-1.1.4-0a.i386.deb
dpkg: error: cannot access archive 'hl3170cdwcupswrapper-1.1.4-0a.i386.deb': No such file or directory
###############################ls: cannot access '/usr/share/ppd/*.ppd': No such file or directory
ls: cannot access '/usr/share/cups/model/*.ppd': No such file or directory
#

0: beh
1: https
2: cups-brf:/
3: hp
4: http
5: lpd
6: serial:/dev/ttyS0?baud=115200
7: socket
8: ipp
9: ipps
10: parallel:/dev/lp0
11: hpfax
12 (I): Specify IP address.
13 (A): Auto. (usb://dev/usblp0)

select the number of destination Device URI. ->12

 enter IP address ->192.168.1.200
lpadmin -p HL3170CDW -v socket://192.168.1.200 -E
Test Print? [y/N] ->y

wait 5s.
lpr -P HL3170CDW /usr/share/cups/data/testprint
Hit Enter/Return key.
rmdir: failed to remove '/tmp/brprinter-installer_OpdOxT': Directory not empty
wayne@guest:~/Utilities/Brother Printer$ 
[/INDENT]

Any help would be appreciated.

---

### Post by ActionParsnip on 2024-03-19
What is the output of:
```

uname -a; lsb_release -a

```
Thanks

---

