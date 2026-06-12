---
title: "Likewise-Open not supporting Samba integration"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gmoore777 on 2010-04-16
On April 5th, Likewise-Open confirmed that they will not support the Samba integration for Lucid platform.

Meaning, you cannot create a Samba share on Linux and get to
it from Windows, via Start-->Run-->\\<machineName>\<shareName>

That defeats the purpose of interopability between Windows
and Linux.

Thus the solution that I chose, is to:
       `sudo apt-get purge likewise-open`

and implement the native solution using winbind and samba.


Now that I got that working, I can't see what
benefit there is to using Likewise-Open, other than it does all the manual configuration steps
for you but then sticks in its own glue which evidently can get in the way when Likewise-Open
decides to not support a feature that comes naturally with samba/winbind.

---

### Post by gmoore777 on 2010-04-16
FYI:
I had initially started a thread at Likewise forum:
    [http://www.likewise.com/community/index.php/forums/viewthread/608/](http://www.likewise.com/community/index.php/forums/viewthread/608/)

and had logged this bug on launchpad:
    [https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/522410](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/522410)

---

### Post by maphew on 2010-04-20
To clarify for people finding this thread: Likewise does support Samba, but only to 3.2. Which means it won't work well with stock Ubuntu Karmic and Lucid (which run samba 3.3 and 3.4 respectively).

---

### Post by gmoore777 on 2010-04-27
I attached a file, SambaIntegrationStepsLucidLynx.odt, 
that lists the pertinent steps I had to do to implement ActiveDirectory Integration and provide Samba shares for Windows asccess, on a LucidLynx machine.
I will paste the contents of that document below this line:
--------------------------------------------------------------

ActiveDirectory integration
 using native Samba and Winbind packages.

In other words, to enable users to log in to Ubuntu Linux with Micro$oft Windows username of DOMAIN\first.last and have it authenticate against the company's ActiveDirectory servers.

In addition, you would like to access from a Windows machine, your home directory on Linux via running this on Windows: Start &#8594; Run  \\hostname\first.last.

Some of these steps you will not need to do, but I found I needed to do them
for various reasons due to specifics about my company's network setup.

Some of the notes are in bash shell syntax as I plucked out the pertinent steps from my master script that pertain to the Samba/Winbind setup.
All commands should be preceded by `sudo`.

I've replaced my company's domain name with “DOMAIN”,
my company's alias for the domain name with “DOMAINALIAS”,
my personal machine's hostname with “machine22”,
the ActiveDirectoryServer machine name with “ADSERVER”,
and my name with “first.last” or “DOMAINALIAS\\first.last”.

1.)
My full Windows username, DOMAIN\first.last has been granted authority 
to add machines to the ActiveDirectory server by my IT organization. 
This is a mandatory step.


2.) Install “samba” and “winbind” packages via:
sudo apt-get install samba winbind


3.) Script begin
#!/bin/bash 
# ensure we capture the short version of the hostname
HOSTNAME_S=$(cat /etc/hostname | sed -e 's,[.].*,,') 
# ensure we capture the long version of the hostname
HOSTNAME_L=$HOSTNAME_S.DOMAIN.com 
BACKSLASH='\\'

4.)
fixHostname	# ensure long form of hostname is in /etc/hostname and in the kernel.
    echo $(cat /etc/hostname | sed -e 's,[.].*,,').DOMAIN.com >/etc/hostname 
    hostname `cat /etc/hostname` 

Contents of /etc/hostname and running `hostname` should be:
machine22.DOMAIN.com

5.)
fix_etc_hosts	# ensure there is no long form of hostname in /etc/hosts (lower or uppercase). 
    sed -i "s,${HOSTNAME_L},," /etc/hosts 
    sed -i "s,${HOSTNAME_S}.DOMAIN.COM,," /etc/hosts 

Beginning part of /etc/hosts should look like this:
127.0.0.1	localhost.localdomain	localhost 
127.0.1.1  machine22 


6.)
dhclient_conf	#  edits to /etc/dhcp3/dhclient.conf [ PROBABLY DOES NOT APPLY TO YOU]
   # due to our DHCP servers suffixing DOMAIN.COM to the value of hostname,
   # I had to edit the /etc/dhcp3/dhclient.conf so that is only uses the short hostname 
   # and not the FQDN. 
      if [ "$(grep -c -i "send host-name \"<hostname>\";" /etc/dhcp3/dhclient.conf)" = "1" ]; then 
          echo "DeskTop Version: Use short host name in send command.\n" 
          sed -i "s,send host-name \"<hostname>\";,#&\nsend host-name \"${HOSTNAME_S}\";," /etc/dhcp3/dhclient.conf 
          dhclient 
      else 
          if [ "$(grep -c -i "^request.*;" /etc/dhcp3/dhclient.conf)" = "1" ]; then 
              echo "Laptop Version: Use short host name in send command.\n" 
              sed -i "s,^request.*;,send host-name \"${HOSTNAME_S}\";\n&," /etc/dhcp3/dhclient.conf 
              dhclient 
      fi 

One line in  /etc/dhcp/dhclient.conf should look like:
send host-name "machine22"; 
rather than 
send host-name "<hostname>"; 
Most likely you don't have to do the above at your location.


7.)
fix_etc_samba_smb_conf	# edits to /etc/samba/smb.conf for active directory authentication 
    sed -i 's;workgroup = WORKGROUP;#&\nworkgroup = DOMAINALIAS\nsecurity = ADS\npassword server = ADSERVER.DOMAIN.com\nrealm = DOMAIN.COM;' /etc/samba/smb.conf 
    # 
    # Following entries to help out with authenticating ActiveDirectory access to SAMBA shares 
    sed -i 's;idmap gid.*;&\nidmap backend = idmap_rid:DOMAINALIAS=50-9999999999\nidmap uid = 50-9999999999\nidmap gid = 50-9999999999\nallow trusted domains = no\nwinbind offline logon = true\ntemplate shell = /bin/bash\ntemplate homedir = /home/%D/%U\nwinbind normalize names = yes;' /etc/samba/smb.conf 
#
    cat <<EOF >> /etc/samba/smb.conf 
[${SHORTNAME}] 
path = ${HOMEPATH} 
read only = no 
valid users = DOMAINALIAS\first.last 
browseable = no 
EOF 

  The above script adds these lines:

   workgroup = DOMAINALIAS 
   security = ADS 
   password server = ADSERVER.DOMAIN.com
   realm = DOMAIN.COM 

   idmap backend = idmap_rid:DOMAINALIAS=50-9999999999 
   idmap uid = 50-9999999999 
   idmap gid = 50-9999999999 
   allow trusted domains = no 
   winbind offline logon = true 
   template shell = /bin/bash 
   template homedir = /home/%D/%U 
   winbind normalize names = yes 

[first.last] 
path = /home/DOMAINALIAS/first.last 
read only = no 
valid users = DOMAINALIAS\first.last
browseable = no 


8.)
fix_pam_common_session  # adds  pam_mkhomedir.so skel=/etc/skel/ umask=0027 
  if  [ "$(grep -c pam_mkhomedir.so /etc/pam.d/common-session)" = "0" ]; then 
    sed -i 's;^session.*required.*pam_permit.so.*;&\nsession    required    pam_mkhomedir.so skel=/etc/skel/ umask=0027;' /etc/pam.d/common-session 
  fi 

One line in /etc/pam.d/common-session should look like:
session    required    pam_mkhomedir.so skel=/etc/skel/ umask=0027 


9.)
fix_nsswitch_conf		# add “winbind” to the passwd and group entries 
  if  [ "$(grep -c "compat winbind" /etc/nsswitch.conf)" = "0" ]; then 
    sed -i 's;passwd:.*compat.*$;& winbind;' /etc/nsswitch.conf 
    sed -i 's;group:.*compat.*$;& winbind;' /etc/nsswitch.conf 
  fi 

Part of the /etc/nsswitch.conf file should look like:
passwd:       compat winbind 
group:          compat winbind 


10.) 
fix_etc_krb5_conf 		# adds necessary domain_realm and encryption types. 
  if  [ "$(grep -c "default_realm = DOMAIN.COM" /etc/krb5.conf)" = "0" ]; then 
    sed -i 's;default_realm =.*;default_realm = DOMAIN.COM;' /etc/krb5.conf 
  fi 

  if  [ "$(grep -c "default_tgs_enctypes = rc4" /etc/krb5.conf)" = "0" ]; then 
    # encryption type of nothing, does not work, and using "aes" does not work. 
    # would get error of: "KDC has no support for encryption type" 
    # "kinit: Preauthentication failed while getting initial credentials" 
    sed -i 's;#.*permitted_enctypes = des3-hmac-sha1.*;&\n    default_tgs_enctypes = rc4\n    default_tkt_enctypes = rc4\n    preferred_enctypes = rc4\n    dns_lookup_kdc = true;' /etc/krb5.conf 
  fi 

Part of /etc/krb5.conf should look like this:
    default_realm = DOMAIN.COM 
    default_tgs_enctypes = rc4 
    default_tkt_enctypes = rc4 
    preferred_enctypes = rc4 
    dns_lookup_kdc = true 


11.) the `net` command

This step will make necessary edits to /etc/pam.d files.

doNetAdsJoin # add machine to ActiveDirectory tree 
      service nmbd stop;  service nmbd start 
      service smbd stop;  service smbd start 
      /etc/init.d/winbind restart 

      kinit [email]first.last@DOMAIN.COM[/email] 

      # need to ensure long form of machine name is in /etc/hosts, for `net` command to work 
  if  [ "$(grep -c -i ${HOSTNAME_L} /etc/hosts)" = "0" ]; then 
    sed -i "s,127.0.1.1.*${HOSTNAME_S},127.0.1.1 ${HOSTNAME_L} ${HOSTNAME_S}," /etc/hosts 
  fi 

      net ADS JOIN -U first.last -S ADSERVER.DOMAIN.com createupn=host/${HOSTNAME_S}@DOMAIN.COM createcomputer="CompanyA Users and Computers/Boston/Workstations/Desktops/Linux" 

      fix_etc_hosts 	# see above
      fixHostname    # see above

      service nmbd stop;  service nmbd start 
      service smbd stop;  service smbd start 
      /etc/init.d/winbind restart 

12.)
Add an ActiveDirectory user to /etc/sudoers:
`sudo visudo`
(initially you will be in an editor that is not “vi”)

Add these lines:

    Defaults editor=/usr/bin/vi 

    DOMAINALIAS\\first.last ALL=(ALL) ALL 


13.) Done
Reboot if you would like then try these:

see if `wbinfo -t` returns:
	checking the trust secret via RPC calls succeeded 

see if `wbinfo -u` and `wbinfo -g` returns all ActiveDirectory users and groups.

See if you can switch user to an ActiveDirectory user:

	su - DOMAINALIAS\\first.last

14.)
Regarding the above step # 11,  the `net` command: if you were amidst ripping out Likewise-open
you may have the problem where installing winbind and the `net` command does not make the necessary edits to the /etc/pam.d files.
Here are the pertinent lines of interest in the 5 /etc/pam.d files that you will need to add or ensure that they are there.

common-account 
account [success=2 new_authtok_reqd=done default=ignore]        pam_unix.so 
account [success=1 new_authtok_reqd=done default=ignore]        pam_winbind.so 

common-auth 
auth    [success=2 default=ignore]      pam_unix.so nullok_secure 
auth    [success=1 default=ignore]      pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass 

common-password 
password        [success=2 default=ignore]      pam_unix.so obscure sha512 
password        [success=1 default=ignore]      pam_winbind.so use_authtok try_first_pass 

common-session 
session optional                        pam_winbind.so 

common-session-noninteractive 
session optional                        pam_winbind.so 


[gmoore777 Last updated on 2010-04-27]

---

### Post by Lucky. on 2010-04-28
A thanks to both of you.  I've spent the past day struggling with this on Karmic, and was wondering why things wouldn't work.  Guess I'll go try winbind instead.

Darn!  Likewise-Open looked like it was a lot simpler to set up.

Thanks again!

---

