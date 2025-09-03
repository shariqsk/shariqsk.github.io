---
title: "The Zocratic MMA Construction Statistics: Learning Project to Production Platform"
date: 2025-09-03
categories: [development, mma, machine-learning]
tags: [fastapi, nextjs, postgresql, aws, machine-learning, web-scraping]
---

## How It All Started

I was lacking any real knowledge on how things worked. I knew the theory, I knew what things were but I never knew it was applied. I decided to create something real rather than reading about it. My friend and I were seeking a project that would allow us to apply the entire stack development skills we were learning and MMA statistics appeared to be the ideal field.

The reason we selected this was because it is a thing that we both love and it is an issue in the real world that needs to be solved. Fight fans desire true statistics, analysts require dependable data, and there is an actual void in the market regarding complete, current MMA data.

## The Technology Choices: Why I Built It This Way

### Backend Architecture

FastAPI was my choice because I wanted something modern and fast, and because it makes you think about data validation and type safety at the very beginning. In cases where you are working with thousands of fighter records, automatic input validation and type checking help eliminate many bugs that would otherwise be security vulnerabilities.

The database was obviously going to be PostgreSQL. I had to have something that could support complex data relationships effectively, and the JSONB support is exactly what I need to store fighter statistics that do not fit well in simple table structures.

### Frontend Decisions

Next.js 15 was ideal to what I wanted to develop. I had to study React correctly, and Next.js provides much of the infrastructure you require by default. The App Router is a much better alternative to the old Pages Router, particularly with regard to performance and SEO.

TypeScript was essential. Type safety helps eliminate runtime errors and makes the codebase far easier to maintain, when you are creating something this complex. I have identified many possible bugs during the development that would have been runtime errors in JavaScript.

### Authentication and Data Store

I used AWS Cognito as an authentication service since it is a battle-tested service that can support the complex security needs that I needed to get correct. Although I can develop user management myself, Cognito offers enterprise-level security features, compliance accreditation, and takes care of edge cases, which are simple to overlook when developing against blank slate.

Supabase handles my database operations, which allows me to concentrate on the development of features rather than on database management. For the backend infrastructure, I'm running on Oracle Cloud, which provides reliable hosting and scaling capabilities. However, I ensure that all security settings have been properly configured and maintained across both platforms.

## The Security Mindset: Why It Counts

### Authentication and Authorization

Creating a platform that individuals can entrust their information to is something that must be secured right at the start. All API endpoints are user authenticated, and I have put in place an adequate rate limit to reduce abuse and possible attacks.

The JWT tokens expire and I have refresh tokens with long sessions. I was taught very early that retrofitting security is far more difficult than security built into the structure.

### Sanitization and Data Validation

Any data that enters the system is validated and sanitized. My backend is based on Pydantic models and my frontend is based on Zod schemas. It is not only about avoiding injection attacks - it is about data integrity and making sure that malicious payloads do not threaten the system.

I also consider the contents to be logged. I needed to resolve a problem where database URLs were being recorded in production - that is the last thing you want to disclose as it can result in security breaches. At this point, I just add what is needed to debug and monitor.

### API Security

I used CORS in a proper way with restrictive policies. It provides the API with trusted origins only and I am using correct HTTP status codes. I also included rate limiting since I do not want the API to be used as a denial of service tool or as a means of abuse.

## The Data Collection Problem

### Why Web Scraping?

There was no open API to simply obtain everything we need, so, we had to find our own using web scraping techniques. However, scraping has its share of problems - web sites evolve and you must be considerate of their servers without breaking any terms of service.

I constructed the scrapers in a strong manner. They deal with page layouts, correct retry logic on unsuccessful requests, and rate limits. Above all, they run at human speed - and natural delays between requests keep them within the terms of service of UFC, and in the future other promotions. I also made them adjustable to allow me to easily alter scraping frequency depending on the frequency of actual changes in the source data.

### Data Quality and Security

The greatest difficulty was not necessarily gathering the data but doing it properly and safely. Not all sources have the same fighter names and some of the statistics are not provided or are in different formats. It was very important to me that we were able to securely bring in data and accurately.

I created a full data cleaning pipeline that normalizes names, authenticates statistics and cross-checks information across several sources. It is not flawless, but it helps to detect most glaring mistakes and avoid any possible security concerns.

## Machine Learning: Why I Built It This Way

### The Leakproof Approach

I am not a data scientist, but I learned enough about the field to realize that data leakage is an actual problem. When you use data that would not have been available during prediction time to train your model, you are basically cheating and developing a model that will not be useful in production.

This is why I designed the feature engineering system into time-aware. It does not depend on information that would have been available after a fight. This may seem obvious, but it is actually quite easy to get wrong, and its consequences on model performance can be far-reaching.

### Feature Engineering

I took much time contemplating the things that really count in a fight. Not only win/loss records, but recent form, styles of fighting, physical advantages, and their interaction with one another.

The system develops applications such as time-weighted recent performance and style matchup compatibility. These properties are intuitively reasonable according to the way fights actually operate, and the model does well with them.

The last time I tuned the features was a while ago. so far our accuray for each event is 65+%. It might be time to give it another look at adjust some things.

## The Predictions Game: The Basic Idea

### Why I Built a Game System

The platform is interesting and the reason behind users returning is the predictions game. Users are able to choose the winners of future fights and the system keeps track on how well they are doing. It is not only about showcasing statistics but rather about making it interactive and allowing people to test their knowledge and compete with others.

The difficulty lay in creating an equal scoring system that would count accuracy as well as consistency. I did not want users to feel that their predictions did not count, and that the system was unjust.

### How the Game Works

Users earn points when they are right, and bonuses when picking underdogs and streaks. The leaderboard displays the people who are doing the best, and the user is able to view their prediction history and accuracy over time.

I also introduced a tier system in which different features can be unlocked by different users depending on their performance. It provides the individuals with the motive to continue to better and interact with the platform.

### Connects with ML Predictions

The game is connected to the machine learning predictions, and thus, the users can monitor what the AI believes about each fight. It is not about usurping human judgment - it is about giving the user more information to help them make better decisions.

## Zobot AI: The Surprise Facility

### Why I Added AI

I was reading the Groq API and considered how the interface with natural language can help make the platform more accessible. The concept was to provide a natural language means of asking questions about fighters, which the average fan could easier digest the data.

I designed Zobot as a context-sensitive and safe robot. It has access to the entire fighter database and is capable of making intelligent analysis. However, I have also introduced extensive safety measures to avoid abuse.

### The Technical Challenges

The greatest dilemma was to make sure that the answers Zobot provided were correct, useful and safe. I took my time to test various prompts and apply adequate rate limiting and error handling. When the Groq API fails I would not like the whole platform to fail.

Some issues which are still pending a fix are the literal Zobot takes data. Israel Adesanya, an amazing striker, was being mistaken as a grade A wrestler because of his takedown success rate and defense rate. I'll need to look into it and try to adjust the instructions to have a bigger effect on these cases. 

## Performance and Scaling: Learning the Hard Way

### Database Optimization

I understood that the performance of the database is vital when it comes to thousands of fighter records and real-time game data. I have added appropriate indexes, query optimization and JSONB to complicated data structures.

Connection pooling and connection management was also introduced by me. These are basic optimizations that have a massive impact on performance.

### Frontend Performance

React Query was also used to fetch and cache data, and it removed unnecessary API calls and enhanced the user experience. I have also used lazy loading of images and the in-built optimization of Next.js.

The animations are fluid since I am working with Framer Motion, but I do not overdo it. Usability and performance are more important than effects.

## Deployment and DevOps: Simple Enough

### Why Vercel and Supabase

I decided to use Vercel on the frontend, as it offers great performance, automatic deployments and decent monitoring without the burden of server management. The world-wide CDN has made the loading to be rapid.

Supabase does a great job at maintaining the back-end infrastructure, so I can concentrate on feature development rather than database administration and authentication processes.

### Observability and Monitoring

I have introduced some simple monitoring which provides me with an insight into the performance and errors of the system. I will write what is needed to debug and monitor, but I will take care not to provide sensitive information.

## What I'd Do Differently

### Planning and Architecture

I would have better planned the schema and API design of the database at the start. There have been a number of refactorings as requirements changed, which is a time-consuming process that could have been prevented with more upfront planning.

### Testing Strategy

I did not do extensive testing in the first place and I am adding tests as I proceed. This would have been more convenient to construct internally initially, particularly where important security and data validation tasks are involved.

### Documentation

I am recording as I construct and I wish I had been more regular about it. Proper documentation helps save a lot of time during debugging or feature addition.

## Business Side: What I Have Learned

### User Feedback is Everything

I have made the majority of my decisions based on the feedback of users. People desired an enhanced search, and I enhanced the search. They desired the predictions game and I constructed that. They demanded mobile optimization and I paid attention.

You can just add features that you believe are cool but unless the people using the product actually use them, what is the point? But, I still tend to add features I find cool time to time because I like them.

### Pricing and Monetization

I am working out the business model. When the platforms scales to a higher userbase it could be expensive to operate (APIs, hosting, etc.), however, I would like to make it available to users. I am thinking of a freemium model with the power user premium features. Currently there is 2 paid tiers, and more features are being curated towards them. 

### Community Building

The predictions game has developed a group of users that engage in fighting and debate. I have found it satisfying to watch individuals interact with the site and form relationships with one another based on their mutual interests.

## The Future: What I Would Like to Do With This

### Short Term (Next 3-6 months)

I would like to enhance mobile experience and introduce more socialization of the predictions game. Predictions and discussing fights are things that users desire to do.

I am also trying to grow beyond UFC to other MMA organizations. It is flexible enough to be handled by the data structure.

### Long Term (6-12 months)

I am thinking of developing a mobile application. The web application is mobile friendly, but native applications could be more suitable to the game functionality.

I also would like to optimize the machine learning predictions. The existing model is not bad, it can be improved.

### The Big Picture

This is what I want MMA statistics and analysis to be. Both hardcore fans and anyone who wants to know what is going on in a fight and play the predictions game to test their knowledge. I want people to be able to come to zocratic before big events, learn and interact with the growing community.

## Advice for Other Developers

### Start Simple, Iterate Fast

Don't attempt to make a complete thing. Begin with the basics and then develop features to the basics as per the feedbacks. Having a small number of features that operate well is better than having a large number of features that are buggy.

### Security First

Consider security at the start. It is far easier to construct it than to attach it afterwards. Proper authentication must be used, all inputs should be validated and care should be taken regarding what you are logging and exposing. This is getting more and more important. The same way you should think mobile first for frontend development, start thinking security first.

### User Feedback is Gold

Listen to your users. They will inform you about what is wrong with your product and what they really want. Do not think you are superior to them.

### Performance Matters

Users are demanding quick responding applications. Speed up your database queries, use adequate caching and test against real machines, not only your development machine.

### Documentation and Testing

Write documentation and tests on the fly. It is not a very exciting task, but it can save a lot of time in the long term.

## Conclusion: What This Project Has Taught Me

The creation of Zocratic MMA Statistics has been an amazing learning process. I heard more about web development, machine learning, and running a production application than I could have ever learned in a tutorial or a course.

That has been the best part of the project because it has developed so much more than I originally intended. It is so gratifying to have a basic notion and see it evolve into something that is in fact used by people.

The predictions game has changed the game. Now it is not only about the presentation of data anymore, but the process of generating an exciting experience that makes users return. It has been very gratifying to see people compete and become better at their predictions.

I am still a student and am still learning and getting better, but I am proud of what we have created. It is not flawless, but it is practical, entertaining, and that is what counts the most.

To anybody considering creating something of the same nature: just start. Select an issue that you feel strongly about, select technologies that you desire to learn, and create something. You will not get it right, but you will learn, and in the long run, you will have something to be proud of.

My current userbase has been extremely helpful when it comes to helping lead me in the right direction on the needs and wants, and hopefully, I cannot wait till be grow even more.
