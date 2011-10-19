These are the additional OCF startup scripts for cluster-agents-1.0.3 package in backports of Debian 5.0 ( Lenny )

Just put them into /usr/lib/ocf/resource.d/heartbeat folder

Example to configure:
###########
HAProxy:
###########
crm configure primitive haproxy ocf:heartbeat:haproxy params conffile=/etc/haproxy/haproxy.cfg op monitor interval=1min

* HAProxy with extra parameters
crm configure primitive haproxy ocf:heartbeat:haproxy params conffile=/etc/haproxy/haproxy.cfg extraconf="-f /etc/haproxy/shared.cfg" op monitor interval=1min

###########
Generic Daemon
###########
Makes it easier to use the same OCF script to start multiple non-OCF aware daemons

Example:
crm configure primitive custom-service1 ocf:heartbeat:generic-daemon params name=service1 op monitor interval="30s"
crm configure primitive custom-service2 ocf:heartbeat:generic-daemon params name=service2 op monitor interval="30s"

* This will start/stop /etc/init.d/service1 ( and monitor pidfile in /var/run/service1.pid ) and /etc/init.d/service2
( and monitor pidfile in /var/run/service2.pid ) 

* If you have a process "httpd" with init file /etc/init.d/apache2 and pidfile in /var/run/httpd/apache.pid, you can do:

crm configure primitive custom-apache ocf:heartbeat:generic-daemon params name=httpd initd="/etc/init.d/apache2" \
 pidfile="/var/run/httpd/apache.pid"  op monitor interval="30s"
