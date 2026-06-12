---
title: "DNS internal external view"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-05-06
I had a SuSE installation with a named.conf and rndc.key file and all zones file in /var/lib/named working.

I tried to re-use that configuration files by:
1. change /etc/default/bind9
> OPTIONS="-u bind -t /var/lib/named"
# Set RESOLVCONF=no to not run resolvconf
RESOLVCONF=yes


2. changed named.conf.local
> acl internals {
	59.124.210.34/28;
	2001:0238:0f00:0009::/64;
    127.0.0.0/8;
    10.0.0.0/8;
    192.168.0.0/16;
};

view "internal" {

	// This should match our internal networks.
	match-clients { internals; };
	// Provide recursive service to internal clients only.
	recursion yes;
// Provide a complete view of the elmit.com zone
// including addresses of internal hosts.

	zone "elmit.com" {
		type master;
		file "elmit.com-internal";
		allow-update { key DHCP_UPDATER; };
	};

....
	zone "9.0.0.0.0.0.f.0.8.3.2.0.1.0.0.2.ip6.int" {
		type master;
		file "2001.0238.0f00.0009.zone";
		allow-update { key DHCP_UPDATER; };
		notify no;
	};

};



view "external" {

	// This should match all
	match-clients { any; };
	// Refuse recursive service to external clients.
	recursion no;
	// Provide a restricted view of the elmit.com zone
	// containing only publicly accessible hosts.

	// Root servers
	zone "." IN {
	        type hint;
        	file "root.hint";
	};

	zone "9.0.0.0.0.0.f.0.8.3.2.0.1.0.0.2.ip6.int" {
		type master;
		file "2001.0238.0f00.0009.zone";
		allow-update { key DHCP_UPDATER; };
		notify no;
	};

                zone "elmit.com" { 
                        type master; 
                        file "elmit.com"; 
		        allow-transfer { 204.74.97.97; 
					204.74.104.10; 
					};
			allow-query { any; };
                };

....

}


and
3. changed rndc.key to 
> // Key for update internal IP's
	key DHCP_UPDATER {
  	  algorithm "hmac-md5";
	  secret "8xfz****************eBxg==";
	};
// key for remote domain name control
key rndc_key {
	algorithm "hmac-md5";
	secret "1xgt*****************guHg==";
};


when I restart bind with
sudo /etc/init.d/bind9 start

I get:
 * Starting domain name service... bind                          [fail] 

with OPTIONS="-u bind" an entry in the message file:
> May  6 17:07:15 dns kernel: [135948.987888] audit(1210064835.548:39): type=1503 operation="capable" name="sys_resource" pid=22307 profile="/usr/sbin/named" namespace="default"
May  6 17:07:15 dns kernel: [135949.000238] audit(1210064835.558:40): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/lib/named/root.hint" pid=22307 profile="/usr/sbin/named" namespace="default"


and with OPTIONS="-u bind -t /var/lib/named" an entry in the message file:
> May  6 17:11:02 dns kernel: [136175.808376] audit(1210065062.795:41): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/lib/named/etc/localtime" pid=22831 profile="/usr/sbin/named" namespace="default"
May  6 17:11:02 dns kernel: [136175.808552] audit(1210065062.795:42): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/lib/named/etc/localtime" pid=22831 profile="/usr/sbin/named" namespace="default"
May  6 17:11:02 dns kernel: [136175.813173] audit(1210065062.805:43): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/lib/named/etc/localtime" pid=22832 profile="/usr/sbin/named" namespace="default"
May  6 17:11:02 dns kernel: [136175.813282] audit(1210065062.805:44): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/lib/named/etc/localtime" pid=22832 profile="/usr/sbin/named" namespace="default"
May  6 17:11:02 dns kernel: [136175.813583] audit(1210065062.805:45): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/lib/named/etc/localtime" pid=22832 profile="/usr/sbin/named" namespace="default"
May  6 17:11:02 dns kernel: [136175.813634] audit(1210065062.805:46): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/lib/named/etc/localtime" pid=22832 profile="/usr/sbin/named" namespace="default"


Even with a liter of coffee, I could not figure out how to change it.

Can anybody give me a hint, please?

bye

R.

---

### Post by ELMIT on 2008-05-06
What does the entry in /var/log/messages mean?

May 6 17:11:02 dns kernel: [136175.813634] audit(1210065062.805:46): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/lib/named/etc/localtime" pid=22832 profile="/usr/sbin/named" namespace="default"

---

### Post by ELMIT on 2008-05-08
While it is not a permanent solution, I have now deleted the entire internal view {} and left only what was within the external view{} and remarked the two statements: match-clients and recursion.

That way it works now! Again, I will need the internal/external view though.
For now at least the external slaves will be feed again.

R.

---

