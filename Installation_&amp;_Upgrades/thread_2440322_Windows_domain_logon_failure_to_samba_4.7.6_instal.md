---
title: "Windows domain logon failure to samba 4.7.6 installed on Ubuntu 18.04"
date: 2020-04-08
forum: Installation &amp; Upgrades
---

### Post by deemix on 2020-04-08
Loooooong Post ahead

Good people.I have a challenge with Samba 4.7.6 installed on my new Ubuntu 18.04 server.
So, Samba has been provisioned using BIND9_DLZ as DNS Backend and i am using FreeBSD's implementation of Kerberos called Heimdall.
Now,here is the first challenge.When i do samba_dnsupdate --verbose --all-names,at the end of the output  i get this 
"Failed 'samba-tool dns' based update of SRV _ldap._tcp.Default-First-Site-Name._sites.ForestDnsZones.nltp-office.com NLTP-DOM-VM.nltp-office.com 389
Failed update of 29 entries
"
In between the output i can also see 
"ERROR(runtime): uncaught exception - (9711, 'WERR_DNS_ERROR_RECORD_ALREADY_EXISTS')"

However,a random check on the DNS entries like 
"host -t SRV _kerberos._tcp.nltp-office.com NLTP-DOM-VM.nltp-office.com" 
shows that the record actually exists in the bind zone file
commands like testparm show that my smb.conf file is OK 
Now,here is the biggest problem i am facing .I just cant add ANY windows machine to the samba domain !
When i try join any machine, i get the following error 
"Logon failure: unknown username or bad password"
I have tried as much to dig into the problem.First stop.Heimdal-kdc's log file.I get to see lines like 
"2020-04-08T08:37:23 Searching referral for nltp-dom-vm.nltp-office.com
2020-04-08T08:37:23 Server not found in database: host/nltp-dom-vm.nltp-office.com@NLTP-OFFICE.COM: no such entry found in hdb
2020-04-08T08:37:23 Failed building TGS-REP to IPv4:192.168.0.250
2020-04-08T08:37:23 tgs-req: sending error: -1765328377 to client"

Then,i start getting these lines 
"2020-04-08T08:49:35 Looking for ENC-TS pa-data -- [email]administrator@NLTP-OFFICE.COM[/email]
2020-04-08T08:49:35 Need to use PA-ENC-TIMESTAMP/PA-PK-AS-REQ
2020-04-08T08:49:35 sending 336 bytes to IPv4:192.168.0.18
2020-04-08T08:49:35 AS-REQ [email]administrator@NLTP-OFFICE.COM[/email] from IPv4:192.168.0.18 for krbtgt/NLTP-OFFICE.COM@NLTP-OFFICE.COM
2020-04-08T08:49:35 Client sent patypes: ENC-TS, 128
2020-04-08T08:49:35 Looking for PK-INIT(ietf) pa-data -- [email]administrator@NLTP-OFFICE.COM[/email]
2020-04-08T08:49:35 Looking for PK-INIT(win2k) pa-data -- [email]administrator@NLTP-OFFICE.COM[/email]
2020-04-08T08:49:35 Looking for ENC-TS pa-data -- [email]administrator@NLTP-OFFICE.COM[/email]
2020-04-08T08:49:35 ENC-TS Pre-authentication succeeded -- [email]administrator@NLTP-OFFICE.COM[/email] using aes256-cts-hmac-sha1-96
2020-04-08T08:49:35 ENC-TS pre-authentication succeeded -- [email]administrator@NLTP-OFFICE.COM[/email]
2020-04-08T08:49:35 AS-REQ authtime: 2020-04-08T08:49:35 starttime: unset endtime: 2020-04-09T08:49:35 renew till: 2020-04-15T08:49:35
2020-04-08T08:49:35 Client supported enctypes: aes256-cts-hmac-sha1-96, aes128-cts-hmac-sha1-96, arcfour-hmac-md5, 24, -135, des-cbc-md5, using aes256-cts-hmac-sha1-96/aes256-cts-hmac-sha1-96
"
This to me means that the login through kerberos is successful.I can confirm this through the klist command which lists an entry for the user administrator!
Then,i check on the /var/log/samba/log.samba file.I get these lines 
"[2020/04/08 10:30:19.565944,  3] ../auth/auth_log.c:760(log_authentication_event_human_readable)
  Auth: [SMB2,NTLMSSP] user [NLTP-OFFICE.COM]\[administrator] at [Wed, 08 Apr 2020 10:30:19.565919 EAT] with [NTLMv1] status [NT_STATUS_OK] workstation [PAC6053-VM] remote host [ipv4:192.168.0.18:50256] became [NLTP-OFFICE]\[Administrator] [S-1-5-21-844398716-371642466-630497442-500]. local host [ipv4:192.168.0.250:445] 
[2020/04/08 10:30:19.566239,  3] ../auth/auth_log.c:220(log_json)
  JSON Authentication: {"timestamp": "2020-04-08T10:30:19.566098+0300", "type": "Authentication", "Authentication": {"version": {"major": 1, "minor": 0}, "status": "NT_STATUS_OK", "localAddress": "ipv4:192.168.0.250:445", "remoteAddress": "ipv4:192.168.0.18:50256", "serviceDescription": "SMB2", "authDescription": "NTLMSSP", "clientDomain": "NLTP-OFFICE.COM", "clientAccount": "administrator", "workstation": "PAC6053-VM", "becameAccount": "Administrator", "becameDomain": "NLTP-OFFICE", "becameSid": "S-1-5-21-844398716-371642466-630497442-500", "mappedAccount": "administrator", "mappedDomain": "NLTP-OFFICE.COM", "netlogonComputer": null, "netlogonTrustAccount": null, "netlogonNegotiateFlags": "0x00000000", "netlogonSecureChannelType": 0, "netlogonTrustAccountSid": "(NULL SID)", "passwordType": "NTLMv1"}}
[2020/04/08 10:30:19.566366,  3] ../auth/auth_log.c:139(get_auth_event_server)
  get_auth_event_server: Failed to find 'auth_event' registered on the message bus to send JSON authentication events to: NT_STATUS_OBJECT_NAME_NOT_FOUND
"
I must say,at this point,i cant really tell where the problem is.Could 
get_auth_event_server: Failed to find 'auth_event' registered on the message bus to send JSON authentication events to: NT_STATUS_OBJECT_NAME_NOT_FOUND
be the issue here? I stand to be guided 
Also,can somebody school me on how authentication from windows machine to samba when doing  domain Join happens?Coz i am very confused now.
This is what i think.When a windows machine is joining a domain,administrative credentials are checked in kerberos,which communicates to Samba if successful then samba sends Domain SID to the joining windows computer and the windows computer updates its registry.What migh i be missing here ?

Please heeeeeelp! .Google,Samba wiki,samba mailing lists,Cyberciti.biz et al have not helped this far

---

### Post by hortimech1 on 2020-04-09
> **deemix said:**
> Loooooong Post ahead

Good people.I have a challenge with Samba 4.7.6 installed on my new Ubuntu 18.04 server.
So, Samba has been provisioned using BIND9_DLZ as DNS Backend and i am using FreeBSD's implementation of Kerberos called Heimdall.

"ERROR(runtime): uncaught exception - (9711, 'WERR_DNS_ERROR_RECORD_ALREADY_EXISTS')"



This sounds like you have installed the 'heimdal-kdc' package, if so then 'apt-get --purge heimdal-kdc' will fix that, Samba comes with its own KDC.

Also the error is just a python error, it shouldn't say anything because you cannot add a dns record that exists.

---

