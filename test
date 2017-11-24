@Bean
	public RestTemplate restTemplate() {
		CloseableHttpClient httpClient = null;
		try {
			httpClient = HttpClientUtils.acceptsUntrustedCertsHttpClient();
		} catch (KeyManagementException | KeyStoreException | NoSuchAlgorithmException e) {
			e.printStackTrace();
		}
		HttpComponentsClientHttpRequestFactory clientHttpRequestFactory = new HttpComponentsClientHttpRequestFactory(
				httpClient);
		List<HttpMessageConverter<?>> messageConverters = new ArrayList<>();
		messageConverters.add(new StringHttpMessageConverter(Charset.forName("UTF-8")));
		messageConverters.add(new FormHttpMessageConverter());
		messageConverters.add(new AllEncompassingFormHttpMessageConverter());
		messageConverters.add(new MappingJackson2XmlHttpMessageConverter());
		messageConverters.add(new MappingJackson2HttpMessageConverter());
		clientHttpRequestFactory.setConnectionRequestTimeout(30000);
		clientHttpRequestFactory.setConnectTimeout(30000);
		clientHttpRequestFactory.setReadTimeout(30000);
		RestTemplate restTemplate = new RestTemplate(clientHttpRequestFactory);
		restTemplate.setMessageConverters(messageConverters);
		return restTemplate;
	}
