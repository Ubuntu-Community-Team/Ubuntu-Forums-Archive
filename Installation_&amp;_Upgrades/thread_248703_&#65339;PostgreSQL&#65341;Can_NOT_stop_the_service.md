---
title: "&#65339;PostgreSQL&#65341;Can NOT stop the service"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by ikenyoung on 2006-09-01
I installed PostgreSQL 8.1.4 by Synaptic. The problem is the db service can not be stopped (or restarted etc. as well) by the treatments listed below:

```

postgres@...$ pg_lsclusters
Version Cluster   Port Status Owner    Data directory                     Log file
8.1     main      5432 online postgres /var/lib/postgresql/8.1/main       /var/log/postgresql/postgresql-8.1-main.log
postgres@...$ pg_ctlcluster 8.1 main stop
Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlcluster line 342.
Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlcluster line 350.
(does not shutdown gracefully, now stopping immediately)

```

In addtion, "psql" and other commands are all available, except "pg_ctl" which can not be found. 

Could anyone help me? Tks

Ken

---

### Post by shahjapan on 2007-07-07
I am having the same problem,

I have installed both 7.4 and 8.1 postgresql server

---

### Post by yohan_y on 2007-07-10
i'm having the same problem using ubuntu 7.04 and postgresql 8.2
still don't know the solution.
but the workaround is to edit pg_ctlcluster file:
1. read the line that makes error
2. sudo gedit /usr/bin/pg_ctlcluster
3. try to understand the perl script a little bit
4. remark lines which cause error

it works for me. i'm having error on line 52.

```
sub check_running_postmaster {
    my $pid = get_running_pid $_[0];
    if (defined $pid and $pid =~ /^\d+$/) {
#  if (open PS, '-|', '/bin/ps', '-o', 'comm', 'h', 'p', $pid) {   // this is line 52
	    my $process = <PS>;
	    chomp $process if defined $process;
	    close PS;
	    if (defined $process and ($process eq 'postmaster' or $process eq 'postgres')) {
                return 1;
            }
# } else {
#            error "Could not exec /bin/ps";
#      }
    }

```

---

