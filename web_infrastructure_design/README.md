# 0-simple_web_stack
**SPOF:**

Everything is running on one server. If anything goes wrong with that server - whether it's a hardware fault, an OS crash, or even a simple configuration error - your entire site goes down.

**Downtime during maintenance:**

When you need to deploy new code or perform any other maintenance tasks, you'll probably need to restart some services, causing temporary downtime.

**Lack of scalability:**

With only one server, you're limited in how much traffic you can handle. If you get a sudden surge in traffic, your server could become overloaded and slow to a crawl or even crash.

# 1-distributed_web_infrastructure
**SPOF:** 

Single points of failure could be the load balancer, or the database if it's not set up with redundancy.

**Security issues:** 

Without firewalls, the servers are open to various attacks. No HTTPS means data is transferred in plain text, which can be intercepted by attackers.

**No monitoring:** 

Without proper monitoring, it can be difficult to identify problems, predict future issues or understand the cause of any downtime.

# 2-secured_and_monitored_web_infrastructure
**SPOF:**

- SSL termination at load balancer: This can create a security vulnerability, because traffic between the load balancer and servers is not encrypted. If an attacker can access this internal network, they can intercept this traffic.
- Single MySQL server accepting writes: This could be a bottleneck. If many requests involve writing to the database, it could slow down response times. It's also a single point of failure; if the write-capable server goes down, no more updates can be made to the database.

**All servers with the same components:** 

Having the database, web server, and application server all on each machine can limit scalability and make maintenance more complex. It's also less efficient use of resources, as different components have different resource needs. A better approach would be to separate these components on different servers or sets of servers, allowing each to be scaled independently.

# 3-optimized_and_scaled_web_infrastructure

We've refined our setup, focusing on security, efficiency, and scalability.

## Server Components Separation:

Web server, application server, and database are now on individual servers for:

- **Efficiency:** Optimal resource allocation.
- **Scalability:** Independent scaling of each component.
- **Maintenance:** Easier updates and modifications.

## Three Load-Balancers:

Three HAproxy load balancers have been added and configured in a cluster:

- **Availability:** Prevents the load balancer from being a single point of failure.
- **Traffic Management:** Enhanced distribution of incoming traffic.

## Additional Server:

A new server has been added for:

- **Capacity:** Improved traffic handling.
- **Reliability:** Decreased service disruption risk.

## Summary:

Our refined infrastructure is now more resilient, scalable, and maintenance-friendly, facilitating better communication and problem resolution.
