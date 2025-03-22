# SMTP Server

Refered Article : <https://valyent.substack.com/p/build-your-own-smtp-server-in-go>

- Simple Mail Transfer Protocol
- Listens on port 25 by Default
- Protocol for sending/Receiving mails over internet

# Email Authentications

1. DKIM -

- Stands for <i><strong>DomainKeys Identified Mail</strong></i>
- It proved that email hasn't been tampered during transit

## Working

- Email added a digital signature to every outgoing email
- Receivers check the signature against the public key published in DNS records
- if signature is valid, the email passes the DKIM check else failed (means email is tampered)

2. SPF -

- Stands for <i><strong>Sender Policy Framework</strong></i>
- Specifies the list of domains which are allowed to send emails on my domain's behalf

## Working

- User publish a list of authorized IP addresses in his/her DNS Server
- When an email arrives claiming to be from your domain, the receiving server checks if it came from an IP on your list.
- If matches, email passes the SPF check

3. DMARC -

- Stands for Domain-based Message Authentication, Reporting and Conformance
- Decides what will happen to the mail that fails the DKIM and SPF checks

## Working

- User sets a policy in their DNS records in which they specifies how to handle emails that fails the Authentications
- Options ranges from "let it in anyways " to "reject it outrights"
- Provides reports in emails authentications results, helping you montior and imporove your email security
- Think it like a Bouncer of your Email
